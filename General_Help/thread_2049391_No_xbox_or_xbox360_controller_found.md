---
title: "No xbox or xbox360 controller found"
date: 2012-08-28
forum: General Help
---

### Post by Geezanansa on 2012-08-28
Trying to run  older games using controller for xbox360 on an older system.

To summarize what is happening 
Running 12.04 precise and using a Razer Onza TE wired usb controller.  
Installed xboxdrv through Ubuntu Software Centre but running xboxdrv  gives No Xbox or Xbox360 controller found.  The driver version being  used is xboxdrv 0.8.2. 

Referring to ```
RUNNING XBOXDRV USING A SINGLE CONTROLLER
       Plug in your Xbox360 gamepad and then unload the xpad driver via:

       $ rmmod xpad

       If  you  want  to  permanently  unload  it  add  the  following line to
       /etc/modprobe.d/blacklist.conf:

       blacklist xpad

       Next you have to load the uinput kernel module which  allows  userspace
       programs  to create virtual input devices and the joydev module handles
       the /dev/input/jsX devices:

       $ modprobe uinput
       $ modprobe joydev

       You also have to make sure that you  have  access  rights  to  /dev/in&#8208;
       put/uinput,  either  add  yourself to the appropriate group, adjust the
       permissions or run xboxdrv as root.

       Once ensured that xpad is out of the way and  everything  is  in  place
       start the userspace driver with:

       $ xboxdrv

       Or  in  case  you  don't have the necessary rights (being in group root
       should often be enough) start the driver as root via:

       $ sudo xboxdrv

       This will create /dev/input/js0 and allow you  to  access  the  gamepad
       from any game. To exit the driver press Ctrl-c.
```The folder dev/input/js0 does exist and jstest-gtk correctly identifies Razer Onza controller.  Does this mean uinput and joydev modules are loaded?.  

How do i unload xpad module in 12.04 precise?  Do i need to? 
 Have tried ```
sudo rmmod xpad
```
(Edit: sudo rmmod xpad unloads xpad module and xboxdrv tells you to do that or use --detach-kernel-driver option.)

How to change permissions on dev/input/js0?  So xboxdrv can use that device.  (Edit: unloading xpad gives xboxdrv access to that device)

Thanks in advance.

---

### Post by Geezanansa on 2012-08-28
Have spent much time researching and learning how to use xboxdrv.    Still not broken anything yet and can get xboxdrv to run xbox360  controller. Was trying to use ```
lsmod
``` to list loaded modules  to make sure xpad was unloaded and that uinput as well as joydev were  loaded.  uinput does not show using ```
lsmod
```

```
lsusb

```gave a device ```
Bus 004 Device 002: ID 1689:fd00
```


so  ```
sudo xboxdrv --device-by-id 1689:fd00 --type xbox360
``` does  get event output in terminal. ```
xboxdrv 0.8.2 -  http://pingus.seul.org/~grumbel/xboxdrv/ 
Copyright © 2008-2011 Ingo Ruhnke <grumbel@gmx.de> 
Licensed under GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html> 
This program comes with ABSOLUTELY NO WARRANTY. 
This is free software, and you are welcome to redistribute it under certain 
conditions; see the file COPYING for details. 

Controller:        unknown
Vendor/Product:    1689:fd00
USB Path:          004:002
Controller Type:   Xbox360

Your Xbox/Xbox360 controller should now be available as:
  /dev/input/js0
  /dev/input/event4

Press Ctrl-c to quit, use '--silent' to suppress the event output

```


So  slight progress is being made.  The goal here is to get xboxdrv mapping  keyboard buttons to controller (or controller buttons to keyboard  lol).  If i press the controller A button i want game to think i pressed  btn_space on keyboard which would make character jump in the game i  intend playing.

Just need to update  src/xpad_device.cpp 
and make config file 
then make start up script for game.
:lolflag:

---

### Post by Geezanansa on 2012-08-29
Getting closer to running the game with xbox controller.

Can not find  src/xpad_device.cpp for autodetection by xboxdrv.
How do i find this file on 12.04 precise with xboxdrv_0.8.2-1_i386.deb installed.

To save runningsudo xboxdrv --device-by-id 1689:fd00 --type xbox360 each time i connect controller;  could try ppa for newer version xboxdrv but safer to go by deb installed by ubuntu software centre i thinks and make a start up script for controller/game.

Have managed to put together an untested config file for Call of Duty
```
[xboxdrv]
silent=true
deadzone=6000
dpad-as-button=true
trigger-as-button=true

[ui-axismap]
x2=REL_X:10
y2=REL_Y:-10
x1=KEY_A:KEY_D
y1=KEY_W:KEY_S

[ui-buttonmap]
tl=KEY_LEFTSHIFT
tr=KEY_LEFTCTRL

[ui-buttonmap]
a=KEY_SPACE
b=KEY_C
x=KEY_1
y=KEY_R

[ui-buttonmap]
lb=KEY_Q
rb=KEY_E

[ui-buttonmap]
lt=BTN_LEFT
rt=BTN_RIGHT

[ui-buttonmap]
dl=KEY_4
dr=KEY_F
du=BTN_MIDDLE
dd=KEY_TAB

[ui-buttonmap]
back=KEY_ESC
start=KEY_ENTER
```

So... all i need to do is > Just need to update  src/xpad_device.cpp 
and make config file 
then make start up script for game.
:lolflag:

How though HOW?
Where is src/xpad_device.cpp?

Back searching net....

---

### Post by Geezanansa on 2012-08-29
So further progress....

xboxdrv was installed by ubuntu software centre which is specifically xboxdrv_0.8.2-1_i386.deb and so this is something to do of why there is no file called src/xpad_device.cpp on this system

regardless of which looking at examples and info in man xboxdrv as well as simply re-editing the config file i had been working on earlier i tried starting xboxdrv with this ```
sudo xboxdrv -s --device-name "Razer Onza TE" --device-by-id 1689:fd00 --type xbox360 \
--deadzone 4000 --dpad-as-button --trigger-as-button --ui-axismap "x2=REL_X:10,y2=REL_Y:10,x1=KEY_A:KEY_D,y1=KEY_W:KEY_S" --ui-buttonmap "tl=KEY_LEFTSHIFT,tr=KEY_LEFTCTRL" --ui-buttonmap "a=KEY_SPACE,b=KEY_C,x=KEY_1,y=KEY_R" --ui-buttonmap "lb=KEY_Q,rb=KEY_E" --ui-buttonmap "lt=BTN_LEFT,rt=BTN_RIGHT" --ui-buttonmap "dl=KEY_4,dr=KEY_B,du=BTN_MIDDLE,dd=KEY_TAB" --ui-buttonmap "back=KEY_ESC,start=KEY_ENTER"
```

:lolflag:and it WORKS 
ROFL:lolflag:

so gonna go off and see if the game is still working.....

---

### Post by Geezanansa on 2012-08-29
:Pyep it really does work RFLOL

---

