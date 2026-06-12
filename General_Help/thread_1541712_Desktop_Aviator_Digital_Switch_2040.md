---
title: "Desktop Aviator Digital Switch 2040"
date: 2010-07-29
forum: General Help
---

### Post by jeff.sadowski on 2010-07-29
I Wanted to use a self made gamepad in linux and was wondering how to start. I have a Desktop Aviator Digital Switch 2040 when I plug it in dmesg shows the following

> 
[269499.776095] usb 2-2: new full speed USB device using uhci_hcd and address 4
[269499.964465] usb 2-2: configuration #1 chosen from 1 choice
[269499.974596] input: Desktop Aviator Digital Switch 2040 as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input10
[269499.974752] generic-usb 0003:6017:3522.0003: input,hidraw0: USB HID v1.01 Joystick [Desktop Aviator Digital Switch 2040] on usb-0000:00:1d.0-2/input0


I installed jstest and jscal but I'm not sure where to go from here?

from the above dmesg I assume the gamepad is device /dev/hidraw0

so I tried jstest /dev/hidraw0
and I get

Driver version is 0.8.0.
jstest is not fully compatible with your kernel. Unable to retrieve button map!
Joystick (Unknown) has 2 axes and 2 buttons.
Testing ... (interrupt to exit)

When I press a button I get

jstest: error reading: Invalid argument
and it terminates.

I tried using jscal but am not sure how to set it up.
There are 20 buttons and no axises

> 
jscal -u 0,20,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20 /dev/hidraw0
jscal: error getting version: Invalid argument


--------------------------------------------------------------

I found a way to use it but It is by making my own program.

I was looking at the output of /dev/hidraw0 using a small c program

> 
#include <stdio.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <fcntl.h>
#include <unistd.h>

int main(int argc,char** argv)
{
int button;
int fd=open("/dev/hidraw0",O_RDONLY);
while(1)
{
 read(fd,&button,sizeof(button));
 printf("%i\n",button);
}
}


after some experimenting I figure out that it was sending 0 when I was holding no buttons, 1 when I was only holding one, two when I was only holding 2, 3 when I was holding buttons 1 and 2 so I realized each button was the bits from the first bit to the 20th bit
It only prints the state change so when I first press a button it will tell me what the current state is. I modified my program as follows

> 
#include <stdio.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <fcntl.h>
#include <unistd.h>
#include <math.h>

int main(int argc,char** argv)
{
int x,y;
int button;
int fd=open("/dev/hidraw0",O_RDONLY);
while(1)
{
read(fd,&button,sizeof(button));
 printf("  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20\n");
 for(x=0;x<20;x++)
 {
  y=(int)pow(2,(double)x);
  if(y&button)
  {
   printf("  1");
  }
  else
  {
   printf("   ");
  }
 }
 printf("\n\n");
}
return 0;
}


I can see now when I press buttons.
At this point I can easily use it in many projects.

I'd like to know how I can use it as a gamepad second interface like I can in windows.

---

