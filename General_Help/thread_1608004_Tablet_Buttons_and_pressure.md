---
title: "Tablet Buttons and pressure"
date: 2010-10-28
forum: General Help
---

### Post by ziocane1 on 2010-10-28
Hallo every body,
I need help with my new tablet silvercrest GTA2000.

I connected the tablet and the system (10.04, 64 bit) seen it like a mouse, but it didn't work correctly. So i followed this posts:

[https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)
[http://ubuntuforums.org/showpost.php?p=9573142&postcount=1](http://ubuntuforums.org/showpost.php?p=9573142&postcount=1)

Now I can use the pen like a mouse (open-close program) but I'm not able to draw with gimp and inkscape. I can select the brush but after that I can't draw. I tried to setup gimp but I haven't got the eraser tool, cursor, pad...

```
ls /dev/input/by-id/
usb-SuYin_Acer_CrystalEye_webcam_CN0314-OV03-VA-R02.00.00-event-if00
usb-WALTOP_International_Corp._Media_Tablet-event-mouse
usb-WALTOP_International_Corp._Media_Tablet-mouse
marco@marco-laptop:~$ 

```This is my /usr/lib/X11/xorg.conf.d/70-wizardpen.conf
```


Section "InputClass"
   Identifier "wizardpen"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/event5"

Option        "Device"    "/dev/input/event5"
Option        "TopX"        "1859"
Option        "TopY"        "0"
Option        "BottomX"    "16194"
Option        "BottomY"    "10837"

Driver "wizardpen"
EndSection

Section "InputClass"
   Identifier "wizardpen ignore mouse dev"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/by-id/usb-WALTOP_International_Corp._Media_Tablet-event-mouse"
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad|WALTOP|Waltop"
   Driver ""
EndSection
```Thankyou to very body

---

### Post by Favux on 2010-10-28
Hi ziocane1,

Your silvercrest GTA2000 is a re-branded Waltop tablet, as you know.  Your 70-wizardpen.conf isn't correct.

See the [Waltop HOW TO]("http://ubuntuforums.org/showpost.php?p=9966110&postcount=1") "Lucid Lynx (10.4)".

---

### Post by ziocane1 on 2010-10-28
Thank you very much, now it seems work better, but...

1-  Why, to emulate the left click, sometimes I have to press with the pen on the tablets (for example to enter on the menu) and sometimes I have to click one of the two buttons?

2- About gimp now the pressure function, but erase toll hasn't appear yet (preference > imput > setup...)

3- I can't do right click on desktop to open "preferences", it seems like the buttons still no working correctly 

My 70-wizardpen.conf now is:

```
Section "InputClass"
    Identifier "WizardPen class"
    MatchIsTablet "on"
    MatchProduct "WALTOP"
    MatchDevicePath "/dev/input/event*"
Driver "wizardpen"

# first four Options set automatically, unless you want to use wizardpen-calibrate
Option  "TopX"  "1859"
Option  "TopY"  "0"
Option  "BottomX"  "16194"
Option  "BottomY"  "10837"

Option  "TopZ"  "0"  # minumum pressure, default is 20?
    # not sure that the default is 20; you should able to treat it as a pressure threshold
    # (or "ZThreshold") using values like 5, 10, or 20 if stylus seems too sensitive

Option  "BottomZ"  "511"  # or "1023"; maximum pressure
    # depending on whether the tablet has 512 or 1024 pressure levels

Option  "Rotate90"  "0"  # or "1"
    # 1 rotates tablet 90 degrees

# following two options set automatically
Option  "ScreenX"  "1280"
Option  "ScreenY"  "1024"

Option  "DebugLevel"  "0"  # or "1" to turn debug on
    # Not sure how many debug levels are available, at a guess 0 - 12

Option  "MouseSpeed"  "30"
    # don't know the allowed range or which are useful

Option  "MouseAccel"  "0"  # or "1"
    # 1 turns acceleration on, useful if you are using the tablet as a "mouse"
    # i.e. using [Option "Mode" "Relative"]

Option  "TPCButton"  "on"  # or "off"
    # on is "tip + buttons" while off is "hover mode" i.e. buttons only

Option  "Mode"  "Absolute"  # or "Relative"
    # I believe this is an available option, "Relative" would make the tablet
    # function like a "mouse"

EndSection

Section "InputClass"
    Identifier "WizardPen ignore mouse dev class"
    MatchIsTablet "on"
    MatchProduct "WALTOP"
    MatchDevicePath "/dev/input/mouse*"
    Option "Ignore" "yes"
EndSection

```Part of my xorg:

```
Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
        Identifier      "WizardPen Tablet"
        Driver          "wizardpen"
        Option          "Device"        "/dev/input/event5"
        Option        "TopX"        "1859"
    Option        "TopY"        "0"
    Option        "BottomX"    "16194"
    Option        "BottomY"    "10837"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
    # generated from default
EndSection

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
#        InputDevice "WizardPen Tablet" "AlwaysCore"
EndSection
```
Thank you, and excuse for my English :(

---

### Post by Favux on 2010-10-28
Hi ziocane1,

> 1- Why, to emulate the left click, sometimes I have to press with the pen on the tablets (for example to enter on the menu) and sometimes I have to click one of the two buttons?

I don't know.
> 2- About gimp now the pressure function, but erase toll hasn't appear yet (preference > imput > setup...)
Your stylus does not have an eraser.  It would be a button on the end of the stylus opposite of the tip.  It slides into the stylus barrel.  Waltop styli do not have erasers as far as I know.  Or do you have one?
> 3- I can't do right click on desktop to open "preferences", it seems like the buttons still no working correctly 
Same as question 1?  Others reported the buttons were working correctly.  Could it be one or more of the Options you've added?  How did it work without all of the Options?

---

### Post by ziocane1 on 2010-10-29
I copied all the options from your link except for the calibration. Now I deleted all this options, the result is that right click on the desktop function, but I can't go to the menu. So probably there are some problems in the 70-wizardpen.conf.

                             ```
Your stylus does not have an eraser.  It would be a button on the  end of the stylus opposite of the tip.  It slides into the stylus  barrel.  Waltop styli do not have erasers as far as I know.  Or do you  have one?
```Probably you are right, I seen it in an how-to and I thought it was the result to reach!

Now I'll make some tests  changing the values of the options. If you have suggestions about what values to change...

Thank you again

------------------------

Edit:

I tried rebooting a lot of times, with your options, and the tablet sometimes work well and sometimes doesn't work....

---

### Post by Favux on 2010-10-29
I wonder if somehow the xorg.conf section is active.  It shouldn't be since you commented out the tablet line in "ServerLayout".  But just in case why don't you comment out the tablet section in xorg.conf too.  If it is somehow active that might account for the inconsistency.

The only Options you should use are the 4 coordinate Options.  And only if you need them to calibrate the tablet.

The other Options are set at the default.  Only use them if you are trying to experiment with them and change the default.  Try adding one at a time, if you didn't before.

I would avoid ScreenX and ScreenY unless you are trying to set up on two monitors.  Those values were just in the manual.  Unless that's what your monitor has.

I would think the ones to try would be TopZ.  Say try changing from 0 to 9 , 14, or 19 (pressure threshold of 10, 15, or 20).  You could also see if changing TPCButton does anything.

---

### Post by ziocane1 on 2010-10-30
Hallo, I'm doing tests...
I remebered that following the officila how-to I did that command:

xinput set-button-map "WizardPen Tablet" 1 2

could be the cause of my problem?

---

### Post by Favux on 2010-10-30
> xinput set-button-map "WizardPen Tablet" 1 2

I don't know because that looks like the default.  If you had used:
```
xinput set-button-map "WizardPen Tablet" 1 3 2
```
then reversing it:
```
xinput set-button-map "WizardPen Tablet" 1 2 3
```
should fix it.  Using the name:
```
xsetpointer -l
```
gives you.  I don't know what the "fix" they list:
```
xinput set-button-map "WizardPen Tablet" 1 0 0
```
is about.  It just seems to shut off the stylus buttons.

---

### Post by ziocane1 on 2010-10-31
Ok, I solved it.
I cleaned mi xorg and I re-installed the xserver-xorg-input-wizardpen.
After that I used yours how-to to modify the xorg.conf.d/70-wizardpen.conf. The only options that I added was my calibration (No pressure, no rotation...).
My xorg is the default one...

Now it works perfectly, I'll put "resolve" in two days if it continue works correctly!

Thank you a lot!!!

---

### Post by Favux on 2010-10-31
Hi ziocane1,

Outstanding!  Nice work.  :)

---

