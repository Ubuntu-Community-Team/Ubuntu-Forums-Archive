---
title: "Sixaxis and Mupen64plus"
date: 2009-12-09
forum: General Help
---

### Post by sethhikari on 2009-12-09
Has anyone been successful in getting a sixaxis to work with muphen. I try to set up the keys but it does not seem to work.

---

### Post by Genkakuzai on 2010-01-14
Apparently no one cares to help the Sixaxis/Dualshock users. I'm a beginner so I don't have a clue how to install drivers or anything else needed. I tried but the only button I can press that Mupen64 recognized for input is the PS Button (center) and after that I click to enter any other button and it just automatically closes as soon as I click whichever N64 button I want to configure. So overall, I'm a failure. :D

---

### Post by jacksterson on 2010-02-07
I've got the same problem, it does it as well with vba-express (the only gba i can even get to work, so don't bother with vbam, I can't even install it correctly).

This is really frustrating, as I've got no games to play anymore since my switch to Ubuntu, and I really want to have SOMETHING to do when I'm not busy...

---

### Post by Jackzor on 2010-02-07
> **jacksterson said:**
> I've got the same problem, it does it as well with vba-express (the only gba i can even get to work, so don't bother with vbam, I can't even install it correctly).

This is really frustrating, as I've got no games to play anymore since my switch to Ubuntu, and I really want to have SOMETHING to do when I'm not busy...

Read :P

---

### Post by jacksterson on 2010-02-07
What do you mean 'read'?

---

### Post by jacksterson on 2010-02-07
Bump.  Really frustrated, I could really use the help, I'm so stumped ; ;, I've tried with two different sixaxis controllers, and they're both really sensitive, they need deadzones or something..

---

### Post by jacksterson on 2010-02-08
Can't anyone help a few schmoes out?

---

### Post by jacksterson on 2010-02-08
-not letting this thread die-
its either I bump this thread, or make a new one, i figure.  But I have the same problem as they do....

---

### Post by switch10 on 2010-02-08
I have some crappy 7 dollar rip off of the six axis controller, and it works great with everything I throw at it.  Including Mupen64 and ZSNES.  There are several controller plugins for Mupen64, maybe try another one.

---

### Post by jacksterson on 2010-02-08
> **switch10 said:**
> I have some crappy 7 dollar rip off of the six axis controller, and it works great with everything I throw at it.  Including Mupen64 and ZSNES.  There are several controller plugins for Mupen64, maybe try another one.

I would, but I'm cheap, this controller was given to me.

Also, its doing it with VBAexpress as well.

---

### Post by jacksterson on 2010-02-09
ker-BUMP

---

### Post by jacksterson on 2010-02-09
-keeping this thread alive-

---

### Post by jacksterson on 2010-02-10
bumpbumpbumpuhdump

---

### Post by jacksterson on 2010-02-10
superbump.

same problems, no solution, google has failed me, and so have you (so far...)

---

### Post by jacksterson on 2010-02-11
bamp

---

### Post by Viper1987 on 2011-03-08
I got it working after much troubleshooting... Edit the config file in ~/.mupen64plus (or wherever yours is) and put in the button layouts... I'm having problems with supertuxkart and eduke32 as well... I'm waiting for a reply on my post regarding the drivers as well :(... Don't give up, Microsoft is a corporate blackhole... Opensource all the way!

---

### Post by RoadRunner72 on 2011-03-17
> **Genkaikuzai said:**
> Apparently no one cares to help the Sixaxis/Dualshock users. I'm a  beginner so I don't have a clue how to install drivers or anything else  needed. I tried but the only button I can press that Mupen64 recognized  for input is the PS Button (center) and after that I click to enter any  other button and it just automatically closes as soon as I click  whichever N64 button I want to configure. So overall, I'm a failure. :grin:

Ok, here we go.

1. I assume you already have paired and configured your sixaxis via USB.  Please plug it in via USB. Then open up a terminal window and type the  following command:

```
user@username:~$ jstest /dev/input/js0
```This should lauch the test procedure  for joystick. Now, focus on one line a press the buttons, one after one. Be aware that every button has an axis function and a button  function. In order to find the right button number, look where it switchs from  "off" to "on". The changing numbers are irrelevant. Note down the number  of each button. Once finished, type Crtl+c. It will close the test  application.

2. Stay in the terminal. You now need to know where Mupen is installed  and go there. If for eyample you have it installed via the package  manager (Ubuntu version: 10.04), just type:
```
user@username:~$ cd /usr/games
``` Lauch Mupen out of the  terminal with this command: ```
user@username/usr/games:$  ./mupen64plus
``` Close the opening window, the information we need  is in the terminal window. Look for the entry where it is marked:
 ```
Config DIR: 
```Remain the pass. This is where we need to go. 

3. Type in the following commands:
```
user@username/usr/games/:$ cd <Config DIR>
user@username/<Config DIR>/:§ ls -a
```There should be an entry  called "blight_input.conf". Open it with your favorite Editor, ie emacs or  nano:
```
user@username/<Config DIR>/: nano blight_input.conf
```Now the data will open up and show the controller set up. 
The principle of the document is simple, you have 4 controllers (from 0 -  3) and you can indiviually match the buttons for each of the four  controllers. On the left side, you have the N64 controller buttons, on  the right side in field "button" you place the number of the button of  your Sixaxis. Remind to remove also the existing configuration  and put a "None" in the other fields, except for "Keys" where you put a  "0". Save and close.

NB: normally, you should not have any  problems to use the sticks of the PS3 controller, the left stick of your  ps3 controller already maps the stick of the N64 controller.

Done. Have great fun with Mupen!

---

### Post by FelixII on 2011-08-31
Thank you RoadRunner72 for this good tutorial. :-)

I wasted some hours trying to calibrate my sixaxis with jscal until I realised it was already calibrated right after I plugged it in. In fact, jscal "destroyed" my calibration somehow.

This is my config file for player 1, maybe someone wants to copy it:
/home/user/.config/mupen64plus/blight_input.conf

[PHP]
[controller 0]
plugged=1
plugin=1
mouse=0
device=0
DPad R=key( 274 ); button( 5 ); axis( None ); hat( None , None ); mouse( None )
DPad L=key( 276 ); button( 7 ); axis( None ); hat( None , None ); mouse( None )
DPad D=key( 275 ); button( 6 ); axis( None ); hat( None , None ); mouse( None )
DPad U=key( 273 ); button( 4 ); axis( None ); hat( None , None ); mouse( None )
Start=key( 0 ); button( 3 ); axis( None ); hat( None , None ); mouse( None )
Z Trig=key( 0 ); button( 9 ); axis( None ); hat( None , None ); mouse( None )
B Button=key( 0 ); button( 13 ); axis( None ); hat( None , None ); mouse( None )
A Button=key( 0 ); button( 14 ); axis( None ); hat( None , None ); mouse( None )
C Button R=key( 0 ); button( None ); axis( 2+ ); hat( None , None ); mouse( None )
C Button L=key( 0 ); button( None ); axis( 2- ); hat( None , None ); mouse( None )
C Button D=key( 0 ); button( None ); axis( 3+ ); hat( None , None ); mouse( None )
C Button U=key( 0 ); button( None ); axis( 3- ); hat( None , None ); mouse( None )
R Trig=key( 0 ); button( 11 ); axis( None ); hat( None , None ); mouse( None )
L Trig=key( 0 ); button( 10 ); axis( None ); hat( None , None ); mouse( None )
Mempak switch=key( 0 ); button( None ); axis( None ); hat( None , None ); mouse( None )
Rumblepak switch=key( 0 ); button( None ); axis( None ); hat( None , None ); mouse( None )
Y Axis=key( 0 , 0 ); button( None , None ); axis( 1- , 1+ ); hat( None , None , None )
X Axis=key( 0 , 0 ); button( None , None ); axis( 0- , 0+ ); hat( None , None , None )
[/PHP]A is mapped to the X Button, B to the circle, Z is mapped to R2, right stick is used for the camera buttons.

Best regards,

Felix

---

