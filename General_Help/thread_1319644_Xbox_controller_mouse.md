---
title: "Xbox controller mouse"
date: 2009-11-08
forum: General Help
---

### Post by truthseer0 on 2009-11-08
Hey, I've been using Ubuntu happily for over a year now though whenever a problem comes up i still feel like a complete noob, here's my problem.
I went and bought an xbox 360 wired controller, a Madcatz one, the only one that i found at Wal-Mart. works fine on the xbox, which was important, but i also want it to work on my computer for two functions. first off as a controller, which i did successfully. Second as an over-glorified mouse, with tons of buttons to do things like open Pidgin and Exaile, my media player. I use Xboxdrv for my xbox controller driver, and have successfully gotten all the buttons to do what i want by mapping the buttons to keys, and also playing around with shortcuts on my system. 
MEAT AND POTATOS:
the left analog stick, which i want to control the mouse with, both does and doesn't work. what it does do is move the mouse, but not the cursor on the screen visually. if i gently wiggle my real mouse while moving the xbox left analog stick, i'll see the mouse move with the stick (along with the small jiggle motion from my real mouse). alone however, the mouse cursor doesn't move, until i jiggle the real mouse, where it will then "jump" to the right location. I've tried so many different things from mapping, to ABS vs REL (ABS has no movement but i was desperate at the time and still am). tried editing my xorg.conf, i've asked two fellow Ubuntu users and my other friend a Gentoo user, none of which have any idea what to tell me anymore.
i just want to have my left analog stick control my mouse visually and functionally. i'm determined to make this work. i'll copy and paste the code i'm using in the script, for my controller to work, below.
thank you in advance,
Truthseer0

#!/bin/bash
gksudo modprobe uinput
sudo modprobe joydev
sudo xboxdrv --type xbox360 --device-by-id 0x1bad:0xf016 -s --deadzone 2500 --dpad-as-button --trigger-as-button --axismap -y2=y2 --ui-axismap x1=REL_X,y1=REL_Y,y2=REL_WHEEL:3:50 --ui-buttonmap a=KEY_PLAYPAUSE,b=KEY_ESC,x=KEY_CALC,y=XK_F4,rb=KEY_LEFTALT,lb=KEY_LEFTCTRL,dl=KEY_LEFT,dr=KEY_RIGHT,du=KEY_UP,dd=KEY_DOWN,lt=KEY_PREVIOUSSONG,rt=KEY_NEXTSONG,guide=KEY_MEDIA,start=KEY_HOMEPAGE,back=KEY_MAIL,tl=XK_Tab,tr=KEY_ENTER

---

### Post by truthseer0 on 2009-11-08
anybody? =\
anything? :'(

---

### Post by truthseer0 on 2009-11-09
bump?

---

