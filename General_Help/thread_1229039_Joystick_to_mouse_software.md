---
title: "Joystick to mouse software"
date: 2009-08-01
forum: General Help
---

### Post by joegill85 on 2009-08-01
I am trying to find a how to install and run two programs that convert joystick actions to mouse movements as I want to find the one most suitable for my needs. 

I have Parkinsons disease and at times have difficulty controlling a mouse because of tremor, being able to use a joystick would make it easier for me to use my pc.

I think I have installed the two programs first Joymouse and the second js2mouse but neither seems to work. 

I have used the terminal command sudo joymouse but all that happens is the folling message appears "I'm happy, starting processing-loop now..." but nothing else.

For js2mouse 
joe@joe-desktop:~$ sudo js2mouse
Number of  axes : 2
Number of  buttons : 4
Driver version : 131328
Joystick name : MOSIC      SPEED-LINK Competition Pro

The joystick is a Speedlink Competition Pro with USB connector.
I am running Ubuntu 9.04 64 bit on a partitioned drive with XP on the first partition.
Hardware as follows

2.3 gigahertz AMD Athlon 64 X2 Dual Core with 256 k primary memory cache 1024k secondary
1920 MB ram
160 gig sata hard drive 
ASUS M2N-VM HDMI Mother board

I have calibrated the joystick. If any additional information is required please let me know

 Any help would be greatly appreciated 

Joe  :P

---

### Post by TorpeJG52 on 2009-08-10
use >  sudo joymouse -i /dev/input/js0 -vv

And tell me what happens then:)

---

### Post by joegill85 on 2009-08-11
Hello out there I tried unsuccessfully to use a standard joystick with the software in Linux, and the prohibitive cost of specialist hardware i.e. joysticks that are designed to interface like a mouse make it difficult for me to justify the expenditure for one these.
 
I have instead decided to invest in a large desk mounted trackball similar to those used in arcades. It  has four buttons that can also be built in. I have used trackballs in the past successfully and as long as I can get the sensitivity right I will be ok. I am going to set it up so one hand controls the the trackball and the other operates the buttons.

I will create a new post with my findings when I have it set up.

Joe

---

### Post by smurphv2 on 2009-08-16
Hi All,

I'm also trying to accomplish the same task. I've installed joymouse and used the following command:

```

sudo joymouse -i /dev/input/js0 -vv 

```

When doing so, the terminal appears to register the use of the joypad or buttons, however there is no mouse movement/reaction. A snippet of some of the output I'm receiving is at the bottom of the message.
 
I'm using a playstation 2 controller with a controller to USB converter, which is working in other applications (emulators, etc). Any help would be greatly appreciated. Thanks.

```

Input:  /dev/input/js0
Output: /dev/joymouse
Creating pipe: /dev/joymouse
joymouse creating pipe: File exists
Open input device: /dev/input/js0
joystick detected: Twin USB Joystick
axes: 6, buttons: 12, driver: 2.1.0

I'm happy, starting processing-loop now...
Wait for pipe for writing...
axis[0]: 0	axis[1]: 0	axis[2]: 0	axis[3]: 0	axis[4]: 0	axis[5]: 0	buttons: 
axis[0]: 0	axis[1]: 0	axis[2]: 0	axis[3]: 0	axis[4]: 0	axis[5]: 0	buttons: 
axis[0]: 0	axis[1]: 0	axis[2]: 0	axis[3]: 0	axis[4]: 0	axis[5]: 0	buttons: 
axis[0]: 0	axis[1]: 0	axis[2]: 0	axis[3]: 0	axis[4]: 0	axis[5]: 0	buttons: 
axis[0]: 0	axis[1]: 0	axis[2]: 0	axis[3]: 0	axis[4]: 0	axis[5]: -32767	buttons: 
axis[0]: 0	axis[1]: 0	axis[2]: 0	axis[3]: 0	axis[4]: 0	axis[5]: 0	buttons: 
axis[0]: 0	axis[1]: 0	axis[2]: 0	axis[3]: 0	axis[4]: -32767axis[5]: 0	buttons: 
axis[0]: 0	axis[1]: 0	axis[2]: 0	axis[3]: 0	axis[4]: 0	axis[5]: 0	buttons: 
axis[0]: 0	axis[1]: 0	axis[2]: 0	axis[3]: 0	axis[4]: 0	axis[5]: 0	buttons: 2 
axis[0]: 0	axis[1]: 0	axis[2]: 0	axis[3]: 0	axis[4]: 0	axis[5]: 0	buttons: 
axis[0]: 0	axis[1]: 0	axis[2]: 0	axis[3]: 0	axis[4]: 0	axis[5]: 0	buttons: 1 
axis[0]: 0	axis[1]: 0	axis[2]: 0	axis[3]: 0	axis[4]: 0	axis[5]: 0	buttons:

```

---

### Post by smurphv2 on 2009-08-16
From joymouse's man page, I added the following to my xorg.conf:

```

#from joymouse man
Section "InputDevice"
        Identifier   "Joystick"
        Driver      "mouse"
        Option      "Protocol"       "ExplorerPS/2"
        Option      "Device"         "/dev/joymouse"
        Option      "SendCoreEvents" "true"
        Option      "ZAxisMapping"       "4 5 6 7"
EndSection

Section "ServerLayout"
	InputDevice "Mouse"      "CorePointer"
        InputDevice "Joystick"
EndSection

```

Doing so results in an error message upon a subsequent login:
> 
Ubuntu is running in low-graphics mode
(EE) Problem parsing the config file
(EE) Error parsing the config file


Is there something different I should have in my xorg.conf (or anywhere else)? My joypad device can be found at /dev/input/js0 and I'm running Ubuntu 9.04. 

Thank you for any suggestions, and let me know if any more information would be helpful.

---

