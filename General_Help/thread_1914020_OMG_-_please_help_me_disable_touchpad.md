---
title: "OMG - please help me disable touchpad"
date: 2012-01-23
forum: General Help
---

### Post by stim on 2012-01-23
I have a Dell XPS 15z with a Cypress touchpad. 

Default ubuntu 11.10 installation does NOT have option to disable touchpad clicks. 


I have large hands that hang over the trackpad while I type.   Consequently, when I type, the trackpad with its SUPER-SENSITIVE click detection, clicks all over the screen, moving my mouse cursor, minimizing windows, moving my text cursor.  

I've been using Ubuntu since 2006, It's enough to make me want to scream, and move to a different distro. How do I disable it?

---

### Post by searchfgold6789 on 2012-01-23
There are instructions here: [https://help.ubuntu.com/community/SynapticsTouchpad#Completely_disabling_Touchpad](https://help.ubuntu.com/community/SynapticsTouchpad#Completely_disabling_Touchpad)

---

### Post by kc1di on 2012-01-23
you can disable it by going to a terminal and typing:

```
sudo synclient TouchPadOff=1
```
To restart it type:
```
sudo synclient TouchPadOff=0
```

or you can install touchpad indicator which allows you to disable the touch pad with a mouse click.

here is the repository use the following commands to install it.

```
sudo add-apt-repository ppa:atareao/atareao
sudo apt-get update
sudo apt-get install touchpad-indicator
```

Hope it helps,
dave

---

### Post by ajgreeny on 2012-01-23
I have that problem on my laptop using lubuntu 11.04.  To simply remove the tap-to-click I ran the command ```
synclient MaxTapTime=0
```no sudo needed.  This just stops the tap-to-click but leaves the touchpad still working in other respects.

You can run this at the start of each session  either in startup aplications with command ```
bash -c "synclient MaxTapTime=0"
``` or by putting it in a shell script and running the script at startup of each session.

---

### Post by stim on 2012-01-23
The touchpad is a **Cypress** touchpad, not **Synaptic**. 

Trust me, I have tried the solutions I could find. 

```
$ synclient 
Couldn't find synaptics properties. No synaptics driver loaded?

```

As far as this link:[https://help.ubuntu.com/community/SynapticsTouchpad#Completely_disabling_Touchpad](https://help.ubuntu.com/community/SynapticsTouchpad#Completely_disabling_Touchpad)  I tried disabling one of the pointers with those instructions, and it resulted in my session being terminated and me being logged out. 


Any idea what of the following list is the laptop touchpad?



```
$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Optical Mouse              	id=12	[slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Generic Wheel Mouse              	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=8	[slave  keyboard (3)]
    &#8627; Power Button                            	id=9	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=10	[slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_2HDM           	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=13	[slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                        	id=15	[slave  keyboard (3)]

```

---

### Post by stim on 2012-01-23
```
xinput set-prop 4 "Device Enabled" 0
```

where "4" is the ID from the post above

```
 Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
```

results in me being logged out from my session.

---

### Post by stim on 2012-01-23
Also, the Touchpad Indicator applet from the PPA above, does nothing when I check/uncheck the options.

---

### Post by kc1di on 2012-01-24
> **stim said:**
> Also, the Touchpad Indicator applet from the PPA above, does nothing when I check/uncheck the options.

Sorry they weren't of any help.  you must have a different touchpad than mine as both those methods work great with my setup here. 
good luck and keep looking someone will have the answer.  When you find it come back and let us know so others hunting for the answer will find it also.

---

### Post by pbrane on 2012-01-24
Maybe this will help...
[http://ubuntuforums.org/showthread.php?t=1912377]("http://ubuntuforums.org/showthread.php?t=1912377")

---

### Post by ajgreeny on 2012-01-24
> **pbrane said:**
> Maybe this will help...
[http://ubuntuforums.org/showthread.php?t=1912377](http://ubuntuforums.org/showthread.php?t=1912377)
Looks like that still uses synclient which the OP says did not work.

@OP.
Have you tried installing the **xserver-xorg-input-synaptics** package to get the synclient utility, just in case it works even on your Cypress touchpad?  Must be worth a try, surely.

---

### Post by pbrane on 2012-01-24
> **ajgreeny said:**
> Looks like that still uses synclient which the OP says did not work.
...

Only to set MaxTapTime. The script uses xinput to enable/disable the touchpad. Probably setting MaxTapTime isn't necessary.

EDIT:
According to this [thread ]("http://ubuntuforums.org/archive/index.php/t-1776254.html")there is no linux driver for the cypress touchpad yet. You may have to wait. Here is the [forum thread]("http://forums.fedoraforum.org/showthread.php?t=267918") I got that first link from.

There is someone working on a linux driver, however I can't find were it's been committed yet.

---

### Post by ajgreeny on 2012-01-24
> **pbrane said:**
> Only to set MaxTapTime. The script uses xinput to enable/disable the touchpad. Probably setting MaxTapTime isn't necessary.
But the OP says in his first post > Default ubuntu 11.10 installation does NOT have option to disable touchpad clicks. 


I have large hands that hang over the trackpad while I type.    Consequently, when I type, the trackpad with its SUPER-SENSITIVE click  detection, clicks all over the screen, moving my mouse cursor,  minimizing windows, moving my text cursor.  so it appears that the tap-to-click is perhaps the biggest problem;  he does not want to totally disable the touchpad all the time.

---

### Post by pbrane on 2012-01-24
> **ajgreeny said:**
> But the OP says in his first post so it appears that the tap-to-click is the biggest problem;  he does not want to totally disable the touchpad.
Point taken.

---

### Post by GraeW on 2012-01-25
dang, hadn't even thought about this idea.. just did the "off" command and now I don't have to worry about my finicky touchpad! Wonder if this will help my other mouse issues..

---

### Post by ajgreeny on 2012-01-26
> **GraeW said:**
> dang, hadn't even thought about this idea.. just did the "off" command and now I don't have to worry about my finicky touchpad! Wonder if this will help my other mouse issues..
What "off" command.  Please give more details as it may help others in future.

---

### Post by jttrs on 2012-07-03
hi all,

sorry for dragging this back up from the dead, but I have the exact same problem as the OP and figured out a (kind of) solution.

I have a Dell XPS 15z running 64bit precise and I was encountering all of the same symptoms as the OP when trying to disable tap-click on my touchpad.

I wasn't able to do that, however, using what the OP did to disable the entire touchpad, I was able to just turn the darn thing off.  Except I didn't use id = 4 when entering xinput set-prop 15 "Device Enabled" 0.

It seems the touchpad isn't really a touchpad as far as ubuntu is concerned, but rather a generic mouse.  Which is why on xlist is shows up as: 
&#9116;   &#8627; ImPS/2 Generic Wheel Mouse                  id=15    [slave  pointer  (2)]

With id =15.

The tldr version:
If you want to disable the touchpad entirely on a Dell XPS 15z, nothing Synaptics related will work for you, you will have to enter:

xinput list

find the ID for the Generic Wheel Mouse and then type:

xinput set-prop 15 "Device Enabled" 0

where 15 is whatever id# it gave you for the wheel mouse.


This is a crude method and requires an external mouse as well as a lot of terminal access (each session turning on or off the touchpad this way).  If someone has a better solution for Dell XPS 15z laptops, I would definitely love to hear it.

---

### Post by MarjaE on 2012-07-05
If it's reading the touchpad as a ps/2 mouse, it's either that or some kind of patch. I know there is a patch for the Alps, I'm not sure about yours.

---

### Post by jttrs on 2012-08-10
I wrote this script and put it in my launcher to toggle the touchpad on or off

```
#!/usr/bin/bash
driver_id=`xinput list | grep "ImPS/2 Generic Wheel Mouse" | awk -F'=' ' { print $2 } ' | awk -F' ' '{print $1}'`
driver_state=`xinput list-props ${driver_id} | grep "Device Enabled" | awk -F':|f' '{print $2}'`

if [ $driver_state = "1" ]; then
    xinput set-prop $driver_id "Device Enabled" 0
else
    xinput set-prop $driver_id "Device Enabled" 1
fi
```

It's annoying when I forget to toggle off after a startup, considering setting it to a hotkey and have default on startup be 'off' since I use an external mouse almost exclusively (because the touchpad is so damn annoying).

---

