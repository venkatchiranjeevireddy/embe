1st question led blinking using 8051: code is 

  

10:33 

#include 
<<<<<<< HEAD

void delay(void); 

  

void main(void) 

{ 

while(1) 

{ 

P1 = 0x00; // Turn ON all LEDs (Active LOW) 

delay(); 

  

P1 = 0xFF; // Turn OFF all LEDs 

delay(); 

} 

} 

  

void delay(void) 

{ 

unsigned int i, j; 

  

for(i = 0; i < 255; i++) 

{ 

for(j = 0; j < 255; j++); 

} 

} 

  

=======
void delay(void);   
void main(void) 
{ 
while(1) 
{ 
P1 = 0x00; // Turn ON all LEDs (Active LOW) 
delay(); 
P1 = 0xFF; // Turn OFF all LEDs 
delay(); 
} 
} 
void delay(void) 
{ 
unsigned int i, j; 
for(i = 0; i < 255; i++) 
{ 
for(j = 0; j < 255; j++); 
} 
} 

>>>>>>> 8f708bb (updated file with content12)
10:34 

diagram idea : p1.0 -> led->groung 

  

 

 

 

 

 

11:01 
<<<<<<< HEAD

Lab 2 - Displaying characters/string on LCD using 8051 microcontroller 

  

11:01 

#include 

sbit RS = P3^0; 

sbit RW = P3^1; 

sbit EN = P3^2; 

  

void delay() 

{ 

int i,j; 

for(i=0;i<100;i++) 

for(j=0;j<1000;j++); 

} 

  

void lcd_cmd(unsigned char cmd) 

{ 

P2 = cmd; // ? send data to P2 

RS = 0; 

RW = 0; 

EN = 1; 

delay(); 

EN = 0; 

} 

  

void lcd_data(unsigned char dat) 

{ 

P2 = dat; // ? send data to P2 

RS = 1; 

RW = 0; 

EN = 1; 

delay(); 

EN = 0; 

} 

  

void lcd_init() 

{ 

lcd_cmd(0x38); // 8-bit, 2 line 

lcd_cmd(0x0C); // display ON 

lcd_cmd(0x01); // clear display 

lcd_cmd(0x06); // entry mode 

} 

  

void lcd_string(char *str) 

{ 

while(*str) 

{ 

lcd_data(*str++); 

} 

} 

  

void main() 

{ 

lcd_init(); 

lcd_string("2023 Batch"); 

  

while(1); 

} 

  

 

11:04 

diagram thing: pin 2.0 to pin 2.7 -> D0,D7 of LM016L and p3.0 to p3.2->rs,rw,e and vss->ground and vdd->power(volt) 
=======
Lab 2 - Displaying characters/string on LCD using 8051 microcontroller 

#include <reg51.h>

sbit RS = P3^0;
sbit RW = P3^1;
sbit EN = P3^2;

void delay()
{
int i,j;
for(i=0;i<100;i++)
for(j=0;j<1000;j++);
}

void lcd_cmd(unsigned char cmd)
{
P2 = cmd; // send data to P2
RS = 0;
RW = 0;
EN = 1;
delay();
EN = 0;
}

void lcd_data(unsigned char dat)
{
P2 = dat; // send data to P2
RS = 1;
RW = 0;
EN = 1;
delay();
EN = 0;
}

void lcd_init()
{
lcd_cmd(0x38); // 8-bit, 2 line
lcd_cmd(0x0C); // display ON
lcd_cmd(0x01); // clear display
lcd_cmd(0x06); // entry mode
}

void lcd_string(char *str)
{
while(*str)
{
lcd_data(*str++);
}
}

void main()
{
lcd_init();
lcd_string("2023 Batch");

while(1);
}

diagram thing: pin 2.0 to pin 2.7 -> D0,D7 of LM016L and p3.0 to p3.2->rs,rw,e and vss->ground and vdd->power(volt) .
>>>>>>> 8f708bb (updated file with content12)

  

 

 

 

 

 

 

13:47 

Lab 3.2 - 8051 Serial Transmission in Embedded C 

<<<<<<< HEAD
  

13:47 

#include 

void main() 

{ 

SCON = 0x50; 

TMOD = 0x20; 

TH1 = 0xFD; 

TR1 = 1; 

  

while(1) 

{ 

SBUF = 'I'; 

while(TI == 0); 

TI = 0; 

} 

} 

  

 

 

 

 

 

 

 

 

 

13:50 

rxd->txd 

  

13:50 

txd->rxd 

  

13:50 

keep 11.0592 
=======
#include <reg51.h>

void main()
{
SCON = 0x50;
TMOD = 0x20;
TH1 = 0xFD;
TR1 = 1;

while(1)
{
SBUF = 'I';
while(TI == 0);
TI = 0;
}
}

rxd->txd

txd->rxd

keep 11.0592
>>>>>>> 8f708bb (updated file with content12)

  

 

 

 

 

 

 

14:07 

Lab 4.2 - Interrupt programming in 8051 - Pgm 1 

<<<<<<< HEAD
  

14:07 

#include sbit SW = P3^2; 

sbit IND = P1^0; 

void Delay() 

{ 

int i = 0, j = 0; 

for(i = 0; i < 100; i++) 

{ 

for(j = 0; j < 1000; j++); 

} 

} 

void extint0() interrupt 0 

{ 

IND = 1; 

Delay(); 

IND = 0; 

Delay(); 

} 

void main() 

{ 

IE = 0x81; 

while(1) 

{ 

P2 = 0x55; 

Delay(); 

P2 = 0xAA; 

Delay(); 

} 

} 

  

14:08 

p1.0->led->ground,, p2.0,02.1->leds->ground,, pin 3.2->switch->ground 

=======
#include <reg51.h>
sbit SW = P3^2;

sbit IND = P1^0;

void Delay()
{
int i = 0, j = 0;
for(i = 0; i < 100; i++)
{
for(j = 0; j < 1000; j++);
}
}

void extint0() interrupt 0
{
IND = 1;
Delay();
IND = 0;
Delay();
}

void main()
{
IE = 0x81;
while(1)
{
P2 = 0x55;
Delay();
P2 = 0xAA;
Delay();
}
}

p1.0->led->ground,, p2.0,02.1->leds->ground,, pin 3.2->switch->ground
>>>>>>> 8f708bb (updated file with content12)
  

 

 

14:21 

Lab 5.2 - Interrupt programming in 8051 - Pgm 3 

<<<<<<< HEAD
  

14:21 

with osciiloscope 

  

14:21 

#include sbit OUT = P2^5; 

sbit INP = P1^7; 

sbit COPY = P1^0; 

void timer0_ISR(void) interrupt 1 

{ 

OUT = !OUT; 

} 

void main() 

{ 

OUT = 0; 

TMOD = 0x02; 

TH0 = 0xD2; 

TL0 = 0xD2; 

EA = 1; 

ET0 = 1; 

TR0 = 1; 

while(1) 

{ 

COPY = INP; 

} 

} 

  

14:24 

p1.1->led->ground,p1.7->switch->ground,, p2.5->b of ossciloscops. 

  

 

 

=======
with osciiloscope 

#include <reg51.h>
sbit OUT = P2^5;

sbit INP = P1^7;

sbit COPY = P1^0;

void timer0_ISR(void) interrupt 1
{
OUT = !OUT;
}

void main()
{
OUT = 0;
TMOD = 0x02;
TH0 = 0xD2;
TL0 = 0xD2;
EA = 1;
ET0 = 1;
TR0 = 1;
while(1)
{
COPY = INP;
}
}

p1.1->led->ground,p1.7->switch->ground,, p2.5->b of ossciloscops.
>>>>>>> 8f708bb (updated file with content12)
 

 

 

 

15:30 

Lab 6.1 - LED blinking in ARM (Port 0 - All 32 pins) 

<<<<<<< HEAD
  

15:31 

#include 

void delay(); 

  

void main() 

{ 

IODIR0 |= 0xFFFFFFFF; // Port 0 is now acting as output pin 

  

while(1) 

{ 

IOSET0 |= 0xFFFFFFFF; // Port 0’s all pins are high now (LED is glowing) 

delay(); 

  

IOCLR0 |= 0xFFFFFFFF; // Port 0’s all pins are low now (LED is OFF) 

delay(); 

} 

} 

  

void delay() 

{ 

unsigned int i; 

for(i = 0; i < 30000; i++); 

} 

  

15:31 

17,19->led->ground. 

=======
#include <lpc214x.h>

void delay();

void main()
{
IODIR0 |= 0xFFFFFFFF; // Port 0 is now acting as output pin 

while(1)
{
IOSET0 |= 0xFFFFFFFF; // Port 0’s all pins are high now (LED is glowing) 
delay();

IOCLR0 |= 0xFFFFFFFF; // Port 0’s all pins are low now (LED is OFF) 
delay();
}
}

void delay()
{
unsigned int i;
for(i = 0; i < 30000; i++);
}

17,19->led->ground.
>>>>>>> 8f708bb (updated file with content12)
  

 

 

 

 

 

 

17:14 

Lab 7.2 - Embedded C code for Interfacing of LCD with LPC 2148 

<<<<<<< HEAD
  

17:14 

#include 
=======
#include <lpc214x.h>
>>>>>>> 8f708bb (updated file with content12)

// Control Pins 

#define EN (1<<7) // P0.7 

#define RS (1<<8) // P0.8 

#define RW (1<<9) // P0.9 

<<<<<<< HEAD
  

void delay() 

{ 

int i; 

for(i=0;i<50000;i++); 

} 

  

// Send Command 

void lcd_cmd(unsigned char cmd) 

{ 

IO1CLR = 0x00FF0000; // Clear P1.16–P1.23 

IO1SET = (cmd << 16); // Send command 

  

IO0CLR = RS; // RS = 0 

IO0CLR = RW; // RW = 0 

  

IO0SET = EN; // EN = 1 

delay(); 

IO0CLR = EN; // EN = 0 

delay(); 

} 

  

// Send Data 

void lcd_data(unsigned char data) 

{ 

IO1CLR = 0x00FF0000; 

IO1SET = (data << 16); // Send data 

  

IO0SET = RS; // RS = 1 

IO0CLR = RW; // RW = 0 

  

IO0SET = EN; 

delay(); 

IO0CLR = EN; 

delay(); 

} 

  

// LCD Init 

void lcd_init() 

{ 

lcd_cmd(0x38); // 8-bit, 2 line 

lcd_cmd(0x0C); // display ON 

lcd_cmd(0x06); // entry mode 

lcd_cmd(0x01); // clear 

} 

  

// String display 

void lcd_string(char *str) 

{ 

while(*str) 

{ 

lcd_data(*str++); 

} 

} 

  

int main() 

{ 

// GPIO configuration 

PINSEL0 = 0x00000000; 

PINSEL1 = 0x00000000; 

  

// P1.16–P1.23 as output (data) 

IO1DIR |= 0x00FF0000; 

  

// P0.7, P0.8, P0.9 as output (control) 

IO0DIR |= (1<<7) | (1<<8) | (1<<9); 

  

delay(); // initial delay 

  

lcd_init(); 

  

lcd_string("My India"); 

  

while(1); 

} 

  

 

 

 

 

=======
void delay() 
{ 
int i; 
for(i=0;i<50000;i++); 
} 

// Send Command 

void lcd_cmd(unsigned char cmd) 
{ 
IO1CLR = 0x00FF0000; // Clear P1.16–P1.23 
IO1SET = (cmd << 16); // Send command 

IO0CLR = RS; // RS = 0 
IO0CLR = RW; // RW = 0 

IO0SET = EN; // EN = 1 
delay(); 
IO0CLR = EN; // EN = 0 
delay(); 
} 

// Send Data 

void lcd_data(unsigned char data) 
{ 
IO1CLR = 0x00FF0000; 
IO1SET = (data << 16); // Send data 

IO0SET = RS; // RS = 1 
IO0CLR = RW; // RW = 0 

IO0SET = EN; 
delay(); 
IO0CLR = EN; 
delay(); 
} 

// LCD Init 

void lcd_init() 
{ 
lcd_cmd(0x38); // 8-bit, 2 line 
lcd_cmd(0x0C); // display ON 
lcd_cmd(0x06); // entry mode 
lcd_cmd(0x01); // clear 
} 

// String display 

void lcd_string(char *str) 
{ 
while(*str) 
{ 
lcd_data(*str++); 
} 
} 

int main() 
{ 
// GPIO configuration 
PINSEL0 = 0x00000000; 
PINSEL1 = 0x00000000; 

// P1.16–P1.23 as output (data) 
IO1DIR |= 0x00FF0000; 

// P0.7, P0.8, P0.9 as output (control) 
IO0DIR |= (1<<7) | (1<<8) | (1<<9); 

delay(); // initial delay 

lcd_init(); 

lcd_string("My India"); 

while(1); 
} 

>>>>>>> 8f708bb (updated file with content12)
17:16 

connections: p0.7->e,p0.8->rs,p0.8->rw,,,p1.16 to p1.22->D0 to D1 

  

17:18 

vdd is 5v and vss,vee-> ground. 

  

 

 

 

 

 

 

 

21:05 

Lab 8.1 - Interfacing of 7-segment display to LPC2138 and displaying numbers 

<<<<<<< HEAD
  

21:06 

#include 
=======
#include <lpc213x.h>
>>>>>>> 8f708bb (updated file with content12)

// Delay function 

void delay(unsigned int count) 
<<<<<<< HEAD

{ 

unsigned int i,j; 

for(i=0;i for(j=0;j<1000;j++); 

} 

  

// Common Cathode codes 

unsigned char seg_code[10] = 

{ 

0x3F, //0 

0x06, //1 

0x5B, //2 

0x4F, //3 

0x66, //4 

0x6D, //5 

0x7D, //6 

0x07, //7 

0x7F, //8 

0x6F //9 

}; 

  

int main(void) 

{ 

int i; 

  

IO0DIR = 0x000000FF; // P0.0–P0.7 output 

  

while(1) 

{ 

for(i=0;i<10;i++) 

{ 

IO0CLR = 0xFF; 

IO0SET = seg_code[i]; 

delay(100); 

} 

} 

} 

  

21:07 

19 to 30->connect straight and ground to different thing. 

  
=======
{ 
unsigned int i,j; 
for(i=0;i<count;i++) 
for(j=0;j<1000;j++); 
} 

// Common Cathode codes 

unsigned char seg_code[10] = 
{ 
0x3F, //0 
0x06, //1 
0x5B, //2 
0x4F, //3 
0x66, //4 
0x6D, //5 
0x7D, //6 
0x07, //7 
0x7F, //8 
0x6F //9 
}; 

int main(void) 
{ 
int i; 

IO0DIR = 0x000000FF; // P0.0–P0.7 output 

while(1) 
{ 
for(i=0;i<10;i++) 
{ 
IO0CLR = 0xFF; 
IO0SET = seg_code[i]; 
delay(100); 
} 
} 
} 

19 to 30->connect straight and ground to different thing.
>>>>>>> 8f708bb (updated file with content12)

 

 

 

 

 

 

 

 

 

 

21:24 

Lab 8.2 - Interfacing of Unipolar stepper motor via driver for LPC 2138 ARM board 

<<<<<<< HEAD
  

21:25 

#include 

unsigned char step_sequence[4] = {0x03, 0x06, 0x0C, 0x09}; 

  

void delay(void) 

{ 

unsigned int i; 

for(i = 0; i < 80000; i++); 

} 

  

int main() 

{ 

int i; 

  

IO0DIR |= 0x0F; 

  

while(1) 

{ 

for(i = 0; i < 4; i++) 

{ 

IO0CLR = 0x0F; 

IO0SET = step_sequence[i]; 

delay(); 

} 

} 

} 

  

21:42 

connection : p0.0 to p0.3->1 to 4 and now uln things 9 -> vcc -> middle of rotator,, 

  
=======
#include <lpc213x.h>

unsigned char step_sequence[4] = {0x03, 0x06, 0x0C, 0x09}; 

void delay(void) 
{ 
unsigned int i; 
for(i = 0; i < 80000; i++); 
} 

int main() 
{ 
int i; 

IO0DIR |= 0x0F; 

while(1) 
{ 
for(i = 0; i < 4; i++) 
{ 
IO0CLR = 0x0F; 
IO0SET = step_sequence[i]; 
delay(); 
} 
} 
} 

connection : p0.0 to p0.3->1 to 4 and now uln things 9 -> vcc -> middle of rotator,,
>>>>>>> 8f708bb (updated file with content12)

4 April 

11:03 

 

 

 

Lab 9 - Serial Transmission between ARM LPC2148 board and PC 

<<<<<<< HEAD
  

11:05 

#include 
=======
#include <lpc214x.h>
>>>>>>> 8f708bb (updated file with content12)

void init(void); 

void delay_ms(int); 

<<<<<<< HEAD
  

int main() 

{ 

int i; 

unsigned char c[] = "Admission 2023 \n"; // Send data by writing to U0THR 

  

init(); 

  

while(1) 

{ 

for(i = 0; i <= 17; i++) 

{ 

U0THR = c[i]; 

while(!(U0LSR & 0x20)); // Check status of one bit of U0LSR 

delay_ms(250); 

} 

} 

} 

  

void init() 

{ 

PINSEL0 = 0x05; 

U0LCR = 0x83; // 8-N-1, enable divisors 

U0DLL = 0x62; // 9600 baud rate 

U0DLM = 0x00; 

U0LCR = 0x03; // 8-N-1, disable divisors 

} 

  

void delay_ms(int x) 

{ 

int a, b; 

for(a = 0; a < x; a++) 

{ 

for(b = 0; b < 3000; b++); 

} 

} 

  

11:07 

p0.0->RXD,pin0.1 -> TXD.... 

  

=======
int main() 
{ 
int i; 
unsigned char c[] = "Admission 2023 \n"; // Send data by writing to U0THR 

init(); 

while(1) 
{ 
for(i = 0; i <= 17; i++) 
{ 
U0THR = c[i]; 
while(!(U0LSR & 0x20)); // Check status of one bit of U0LSR 
delay_ms(250); 
} 
} 
} 

void init() 
{ 
PINSEL0 = 0x05; 
U0LCR = 0x83; // 8-N-1, enable divisors 
U0DLL = 0x62; // 9600 baud rate 
U0DLM = 0x00; 
U0LCR = 0x03; // 8-N-1, disable divisors 
} 

void delay_ms(int x) 
{ 
int a, b; 
for(a = 0; a < x; a++) 
{ 
for(b = 0; b < 3000; b++); 
} 
} 

p0.0->RXD,pin0.1 -> TXD....
>>>>>>> 8f708bb (updated file with content12)
11:08 

virtual terminal. 

  

<<<<<<< HEAD
=======





>>>>>>> 8f708bb (updated file with content12)
5 April 

09:03 

<<<<<<< HEAD
#include 

void main() 

{ 

SCON = 0x50; 

TMOD = 0x20; 

TH1 = 0xFD; 

TR1 = 1; 

  

while(1) 

{ 

SBUF = 'I'; 

while(TI == 0); 

TI = 0; 

} 

} 

  

09:16 

for serial transmisson for print string in terminal in 8051:#include 

void main() 

{ 

int i; 

char msg[] = "I love india"; 

  

SCON = 0x50; 

TMOD = 0x20; 

TH1 = 0xFD; 

TR1 = 1; 

  

while(1) 

{ 

for(i = 0; msg[i] != '\0'; i++) 

{ 

SBUF = msg[i]; 

while(TI == 0); 

TI = 0; 

} 

} 

} 

=======
#include <reg51.h>

void main()
{
SCON = 0x50;
TMOD = 0x20;
TH1 = 0xFD;
TR1 = 1;

while(1)
{
SBUF = 'I';
while(TI == 0);
TI = 0;
}
}

09:16

for serial transmisson for print string in terminal in 8051:
#include <reg51.h>

void main()
{
int i;
char msg[] = "I love india";

SCON = 0x50;
TMOD = 0x20;
TH1 = 0xFD;
TR1 = 1;

while(1)
{
for(i = 0; msg[i] != '\0'; i++)
{
SBUF = msg[i];
while(TI == 0);
TI = 0;
}
}
}
>>>>>>> 8f708bb (updated file with content12)
  

13:32 

 

 

 

 

 

 

 

 

 

Lab 4.1 - Controlling LEDs connected to 8051 𝛍C 

<<<<<<< HEAD
  

13:32 

#include 

void delay_5s(void); 

  

int main(void) 

{ 

int i, j; 

  

IO0DIR = 0x000000FF; // Make P0.0–P0.7 as output (LEDs) 

  

for(i = 0; i < 5; i++) 

{ 

IO0SET = 0x00000055; // Even LEDs ON 

IO0CLR = 0x000000AA; // Ensure others OFF 

delay_5s(); 

  

IO0SET = 0x000000AA; // Odd LEDs ON 

IO0CLR = 0x00000055; 

delay_5s(); 

} 

  

while(1); 

} 

  

//-------------------------------------- 

// Rough 5-second delay (software loop) 

//-------------------------------------- 

void delay_5s(void) 

{ 

int i, j; 

  

for(i = 0; i < 5000; i++) 

{ 

for(j = 0; j < 600; j++); 

} 

} 

=======
#include <lpc214x.h>

void delay_5s(void); 

int main(void) 
{ 
int i, j; 

IO0DIR = 0x000000FF; // Make P0.0–P0.7 as output (LEDs) 

for(i = 0; i < 5; i++) 
{ 
IO0SET = 0x00000055; // Even LEDs ON 
IO0CLR = 0x000000AA; // Ensure others OFF 
delay_5s(); 

IO0SET = 0x000000AA; // Odd LEDs ON 
IO0CLR = 0x00000055; 
delay_5s(); 
} 

while(1); 
} 

//-------------------------------------- 
// Rough 5-second delay (software loop) 
//-------------------------------------- 

void delay_5s(void) 
{ 
int i, j; 

for(i = 0; i < 5000; i++) 
{ 
for(j = 0; j < 600; j++); 
} 
} 
>>>>>>> 8f708bb (updated file with content12)
  

13:32 

<<<<<<< HEAD
#include 

void delay_5s(void); 

  

void main() 

{ 

unsigned char r6 = 5; 

  

TMOD = 0x01; // Timer0 Mode1 

  

while(r6--) 

{ 

P1 = 0x55; // Even LEDs 

delay_5s(); 

  

P1 = 0xAA; // Odd LEDs 

delay_5s(); 

} 

  

while(1); 

} 

  

void delay_5s(void) 

{ 

unsigned char r5; 

  

for(r5 = 0; r5 < 100; r5++) 

{ 

TR0 = 0; // ? Stop timer FIRST 

TF0 = 0; // ? Clear flag BEFORE starting 

  

TH0 = 0x3C; // Reload every time 

TL0 = 0xB0; 

  

TR0 = 1; // Start timer 

  

while(TF0 == 0); // Wait overflow 

  

TR0 = 0; // Stop again (safe) 

TF0 = 0; // Clear again 

} 

} 

=======

8051 


#include <reg51.h>

void delay_5s(void); 

void main() 
{ 
unsigned char r6 = 5; 

TMOD = 0x01; // Timer0 Mode1 

while(r6--) 
{ 
P1 = 0x55; // Even LEDs 
delay_5s(); 

P1 = 0xAA; // Odd LEDs 
delay_5s(); 
} 

while(1); 
} 

void delay_5s(void) 
{ 
unsigned char r5; 

for(r5 = 0; r5 < 100; r5++) 
{ 
TR0 = 0; // Stop timer FIRST 
TF0 = 0; // Clear flag BEFORE starting 

TH0 = 0x3C; // Reload every time 
TL0 = 0xB0; 

TR0 = 1; // Start timer 

while(TF0 == 0); // Wait overflow 

TR0 = 0; // Stop again (safe) 
TF0 = 0; // Clear again 
} 
} 
>>>>>>> 8f708bb (updated file with content12)
  

13:32 

 

 

 

 

 

Lab 5.1 Interrupt driven LED and LCD operations using 8051 MCU 

<<<<<<< HEAD
  

13:32 

#include 

#define LCD P2 

  

sbit RS = P3^0; 

sbit RW = P3^1; 

sbit EN = P3^2; 

sbit LED = P1^0; 

  

unsigned char count = 0; 

  

void delay() 

{ 

unsigned char i,j; 

for(i=0;i<255;i++) 

for(j=0;j<255;j++); 

} 

  

void lcd_cmd(unsigned char cmd) 

{ 

LCD = cmd; 

RS=0; RW=0; 

EN=1; delay(); EN=0; 

} 

  

void lcd_data(unsigned char dat) 

{ 

LCD = dat; 

RS=1; RW=0; 

EN=1; delay(); EN=0; 

} 

  

void lcd_init() 

{ 

lcd_cmd(0x38); 

lcd_cmd(0x0C); 

lcd_cmd(0x01); 

lcd_cmd(0x06); 

} 

  

// TIMER ISR 

void timer0_ISR(void) interrupt 1 

{ 

TR0 = 0; 

  

TH0 = 0x3C; 

TL0 = 0xB0; 

  

count++; 

LED = ~LED; 

  

lcd_cmd(0x01); 

lcd_data(count + 0x30); 

  

if(count == 5) 

{ 

ET0 = 0; 

TR0 = 0; 

} 

else 

{ 

TR0 = 1; 

} 

} 

  

void main() 

{ 

lcd_init(); 

  

TMOD = 0x01; 

TH0 = 0x3C; 

TL0 = 0xB0; 

  

ET0 = 1; 

EA = 1; 

TR0 = 1; 

  

while(1); 

} 

  

13:33 

connection same as display and p0.0 to led and ground. 

  
=======
#include <reg51.h>

#define LCD P2 

sbit RS = P3^0; 
sbit RW = P3^1; 
sbit EN = P3^2; 
sbit LED = P1^0; 

unsigned char count = 0; 

void delay() 
{ 
unsigned char i,j; 
for(i=0;i<255;i++) 
for(j=0;j<255;j++); 
} 

void lcd_cmd(unsigned char cmd) 
{ 
LCD = cmd; 
RS=0; RW=0; 
EN=1; delay(); EN=0; 
} 

void lcd_data(unsigned char dat) 
{ 
LCD = dat; 
RS=1; RW=0; 
EN=1; delay(); EN=0; 
} 

void lcd_init() 
{ 
lcd_cmd(0x38); 
lcd_cmd(0x0C); 
lcd_cmd(0x01); 
lcd_cmd(0x06); 
} 

// TIMER ISR 

void timer0_ISR(void) interrupt 1 
{ 
TR0 = 0; 

TH0 = 0x3C; 
TL0 = 0xB0; 

count++; 
LED = ~LED; 

lcd_cmd(0x01); 
lcd_data(count + 0x30); 

if(count == 5) 
{ 
ET0 = 0; 
TR0 = 0; 
} 
else 
{ 
TR0 = 1; 
} 
} 

void main() 
{ 
lcd_init(); 

TMOD = 0x01; 
TH0 = 0x3C; 
TL0 = 0xB0; 

ET0 = 1; 
EA = 1; 
TR0 = 1; 

while(1); 
} 

connection same as display and p0.0 to led and ground.
>>>>>>> 8f708bb (updated file with content12)

14:25 

 

 

 

 

 

 

 

 

Lab 5.2 - Interrupt programming in 8051 - Pgm 3 in arm 

<<<<<<< HEAD
  

14:26 

#include 

#define IN (1<<7) // P0.7 

#define OUT (1<<0) // P0.0 

#define SQ (1<<5) // P0.5 

  

int main() 

{ 

PINSEL0 = 0x00000000; 

  

IO0DIR |= OUT | SQ; // Output 

IO0DIR &= ~IN; // Input 

  

// Timer0 setup 

T0PR = 14; // 1 µs (15 MHz clock) 

T0MR0 = 50; // 50 µs 

T0MCR = 3; // Interrupt + reset 

T0TCR = 1; // Start timer 

  

while(1) 

{ 

// Copy input 

if(IO0PIN & IN) 

IO0SET = OUT; 

else 

IO0CLR = OUT; 

  

// Square wave 

if(T0IR & 1) 

{ 

IO0PIN ^= SQ; 

T0IR = 1; 

} 

} 

} 

  

14:27 

p0.0->led-> ground,,p0.5->a and p0.7->switch.... 

  
=======
#include <lpc214x.h>

#define IN (1<<7) // P0.7 
#define OUT (1<<0) // P0.0 
#define SQ (1<<5) // P0.5 

int main() 
{ 
PINSEL0 = 0x00000000; 

IO0DIR |= OUT | SQ; // Output 
IO0DIR &= ~IN; // Input 

// Timer0 setup 
T0PR = 14; // 1 µs (15 MHz clock) 
T0MR0 = 50; // 50 µs 
T0MCR = 3; // Interrupt + reset 
T0TCR = 1; // Start timer 

while(1) 
{ 
// Copy input 
if(IO0PIN & IN) 
IO0SET = OUT; 
else 
IO0CLR = OUT; 

// Square wave 
if(T0IR & 1) 
{ 
IO0PIN ^= SQ; 
T0IR = 1; 
} 
} 
} 

p0.0->led-> ground,,p0.5->a and p0.7->switch....

  






>>>>>>> 8f708bb (updated file with content12)

15:11 

Lab 8.2 - Interfacing of Unipolar stepper motor via driver for LPC 2138 in 8051. 

<<<<<<< HEAD
  

15:11 

#include 

unsigned char step[8] = { 

0x01, 0x03, 0x02, 0x06, 

0x04, 0x0C, 0x08, 0x09 

}; 

  

void delay(unsigned int ms) 

{ 

unsigned int i,j; 

for(i=0;i for(j=0;j<1000;j++); 

} 

  

void main() 

{ 

int i; 

  

while(1) 

{ 

for(i=0;i<8;i++) 

{ 

P1 = step[i]; 

delay(5); 

} 

} 

} 

  

15:12 

connection p0.0 to p0.3 continuous. 

  
=======
#include <reg51.h>

unsigned char step[8] = { 
0x01, 0x03, 0x02, 0x06, 
0x04, 0x0C, 0x08, 0x09 
}; 

void delay(unsigned int ms) 
{ 
unsigned int i,j; 
for(i=0;i<ms;i++) 
for(j=0;j<1000;j++); 
} 

void main() 
{ 
int i; 

while(1) 
{ 
for(i=0;i<8;i++) 
{ 
P1 = step[i]; 
delay(5); 
} 
} 
} 

connection p0.0 to p0.3 continuous.

  




>>>>>>> 8f708bb (updated file with content12)

15:20 

Lab 8.1 - Interfacing of 7-segment display to LPC2138 and displaying numbers with 8051. 

<<<<<<< HEAD
  

15:20 

#include 

unsigned char seg[10] = { 

0x3F, 0x06, 0x5B, 0x4F, 0x66, 

0x6D, 0x7D, 0x07, 0x7F, 0x6F 

}; 

  

void delay(unsigned int ms) 

{ 

unsigned int i,j; 

for(i=0;i for(j=0;j<1000;j++); 

} 

  

void main() 

{ 

int i; 

  

while(1) 

{ 

for(i=0;i<10;i++) 

{ 

P1 = seg[i]; 

delay(500); 

} 

} 

} 

  

15:26 

p1.0 to p1.7 connects line by line thats it. 
=======
#include <reg51.h>

unsigned char seg[10] = { 
0x3F, 0x06, 0x5B, 0x4F, 0x66, 
0x6D, 0x7D, 0x07, 0x7F, 0x6F 
}; 

void delay(unsigned int ms) 
{ 
unsigned int i,j; 
for(i=0;i<ms;i++) 
for(j=0;j<1000;j++); 
} 

void main() 
{ 
int i; 

while(1) 
{ 
for(i=0;i<10;i++) 
{ 
P1 = seg[i]; 
delay(500); 
} 
} 
} 

p1.0 to p1.7 connects line by line thats it.
>>>>>>> 8f708bb (updated file with content12)
