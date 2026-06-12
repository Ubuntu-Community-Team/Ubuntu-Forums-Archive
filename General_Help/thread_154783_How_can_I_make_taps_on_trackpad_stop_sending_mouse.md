---
title: "How can I make taps on trackpad stop sending mouse clicks"
date: 2006-04-03
forum: General Help
---

### Post by rhomsy on 2006-04-03
Now don't get me wrong, I'm very impressed that ubuntu properly recognized the trackpad and even allows mouse clicks by tapping on the pad.  However, that feature just drives me crazy.  It's making me screw up so many things.  How can I turn this feature off?

Thanks in advance

---

### Post by evilgold on 2006-04-03
interesting question... I found this on an faq about the synaptics driver...

How can I configure tap-to-click behavior?

   1. If you set MaxTapTime=0 in the X config file then the touchpad will not use tapping at all, i.e. touching/tapping will not be taken as a mouse click.
   2. If, instead, you set MaxTapMove=0 in the X config file, then the touchpad will not use tapping for a single finger tap (left mouse button click) but will for the two and three finger tap (middle and right button click).


So I suppose the solution would be to find the correct line in your xorg.conf and set it as MaxTapTime=0

I havnt tried it myself, i like the tap feature... I even have support for the scroller on the side of my pad :-)

---

### Post by nanotube on 2006-04-04
evilgold gives good info - but i think that only works if you have a synaptics touchpad (which is most common, anyway). 
for more context as to where to stick those MaxTapTime lines, check out the link in my sig, and go to the "disable tap click" section. :)

---

### Post by arekmenner on 2006-04-06
Evilgold and Nanotube gave a great method of turning off the touchpad tap on a Synaptics touchpad. If, for any reason, that didn't work, here is another possible approach. Note that I wrote this in a very basic way not to patronize, but to make it easy.
[LIST=1]
[*]Open the file /etc/X11/xorg.conf in your favorite text editor (VIM here). This is where the configuration for your touchpad, along with many other things, is. ```
sudo vi /etc/X11/xorg.conf
```**Note:** You must use sudo to edit this file, otherwise you won't have the proper permissions to save your settings.
[*]Locate the area of the file that configures your touchpad. It should currently look something like this: ```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection
```
[*]Add the property SHMConfig as on to allow you to configure the touchpad. Your file should now look something like this:
```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "on"
EndSection
```
[*]Restart X so your settings will be applied (Alt+E resets X, restarting your whole computer works, too)
[*]Now you can change the property tapbutton, which controls the touchpad tap. ```
synclient TapButton1=0
```
[/LIST]
Okay, now try tapping around. Your tapping should be disabled. If not, perhaps your touchpad is another make, in which case I have little experience. Best of luck!

---

### Post by Morphius on 2006-06-02
If you are running dapper there is a known bug that will cause mouse issues for synaptic pads.

[https://launchpad.net/distros/ubuntu/+bug/47971](https://launchpad.net/distros/ubuntu/+bug/47971)

Check out the link for a work around.

---

### Post by greekgoddj on 2007-03-31
Hello!

```
synclient TapButton1=0
``` works fine for me, but I have to do it everytime I restart the computer. How can I set it for good? thanks

---

### Post by nanotube on 2007-03-31
> **greekgoddj said:**
> Hello!

```
synclient TapButton1=0
``` works fine for me, but I have to do it everytime I restart the computer. How can I set it for good? thanks

easiest way is to just put that command into System>Preferences>Sessions>Startup Programs

---

### Post by Draciron on 2008-04-07
> **greekgoddj said:**
> Hello!

```
synclient TapButton1=0
``` works fine for me, but I have to do it everytime I restart the computer. How can I set it for good? thanks

To make the change perm you can add this line, to /etc/X11/xorg.conf
Option   "TapButton1"         "0"

Restart X and no more annoying accidental clicks. I found my laptop almost unusable until I disabled the taps. 


Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizEdgeScroll"       "0"
        Option           "SHMConfig"            "on"
        Option          "TapButton1"            "0"
EndSection

---

### Post by tempest on 2008-04-07
I don't recall seeing this in gutsy, but in hardy I have a "touchpad" tab in the mouse control panel. On this tab there is a checkbox to disable touchpad clicks. I can use the touchpad buttons now but don't have to worry about accidental clicks on the pad itself.

---

### Post by nanotube on 2008-04-08
> **tempest said:**
> I don't recall seeing this in gutsy, but in hardy I have a "touchpad" tab in the mouse control panel. On this tab there is a checkbox to disable touchpad clicks. I can use the touchpad buttons now but don't have to worry about accidental clicks on the pad itself.

so, ubuntu is improving by leaps and bounds, eh? :) i'm using feisty, and there's no gui for this here.

---

