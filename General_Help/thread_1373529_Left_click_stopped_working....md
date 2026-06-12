---
title: "Left click stopped working..."
date: 2010-01-05
forum: General Help
---

### Post by faceless-21 on 2010-01-05
Hey guys I did an internet upgrade last night and right around then I think I also got a little liquid around the touch-pad of my laptop and now the left click won't work in Ubuntu on either my touch-pad OR mouse so I am not sure if maybe the connection for the left click on the touch-pad is shorted causing it to stay "clicked" which somehow disables the left click on the mouse...  On my windows xp partition(which I am using now) I am able to use the left click on the mouse but still not the touchpad...  Anyway I am wondering if there is a way to disable to touchpad via console or some other way to get around this so I can back my important docs and files and then "mouse" it till I can get a new laptop...?

  Thanks for any help :)

---

### Post by lyall on 2010-01-05
> **faceless-21 said:**
> Hey guys I did an internet upgrade last night and right around then I think I also got a little liquid around the touch-pad of my laptop and now the left click won't work in Ubuntu on either my touch-pad OR mouse so I am not sure if maybe the connection for the left click on the touch-pad is shorted causing it to stay "clicked" which somehow disables the left click on the mouse...  On my windows xp partition(which I am using now) I am able to use the left click on the mouse but still not the touchpad...  Anyway I am wondering if there is a way to disable to touchpad via console or some other way to get around this so I can back my important docs and files and then "mouse" it till I can get a new laptop...?

  Thanks for any help :)

Check Synaptic for touchpad and got this

[I]Synaptics TouchPad driver for X.Org server

This package provides an input driver for the X.Org X server to enable
advanced features of the Synaptics Touchpad including:

 * Movement with adjustable, non-linear acceleration and speed
 * Button events through short touching of the touchpad
 * Double-Button events through double short touching of the touchpad
 * Dragging through short touching and holding down the finger on the touchpad
 * Middle and right button events on the upper and lower corner of the touchpad
 * Vertical scrolling (button four and five events) through moving the finger
   on the right side of the touchpad
 * The up/down button sends button four/five events
 * Horizontal scrolling (button six and seven events) through moving the finger
   on the lower side of the touchpad
 * The multi-buttons send button four/five events, and six/seven events for
   horizontal scrolling
 * Adjustable finger detection
 * Multifinger taps: two finger for middle button and three finger for right
   button events. (Needs hardware support. Not all models implement this
   feature.)
 * Run-time configuration using shared memory. This means you can change
   parameter settings without restarting the X server (see synclient(1)).
 * It also provides a daemon to disable touchpad while typing at the keyboard
   and thus avoid unwanted mouse movements (see syndaemon(1)).


Canonical provides critical updates for xserver-xorg-input-synaptics until April 2011.
[/I]
[I][B]the above info was copied into this 
[/B][/I]
Check to see want other touchpad software that is installed on your laptop.  It will be a place to start checking

Also check the Mouse by going to System > Preferences > Mouse

to test your double click setting, try to doulbe-click on the light bulb at the bottom of the General tab.  

If the right click works, you can switch to Left-handed to try to help you get around to help solve your problem.


if the touchpad works with Windows XP, I would think that it is not a hardware problem.

What kind of laptop is it and model? 


good luck and have fun learning

---

### Post by faceless-21 on 2010-01-05
The touchpad itself works in both windows and ubuntu, but the left click button nor "tapping" works in either...  Also I am unable to access the Sys/Pref/Mouse because I cant left click...  is there a console command to open the Mouse settings?

---

### Post by john newbuntu on 2010-01-05
xinput list
will list the set of input devices.  In there you would probably see Synaptics and an "id" corresponding to that.
xinput list-props <id>
will give the properties for that device.

To disable touchpad, something like this command should work:
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 8 0
You have to replace the "SynPS/2 Synaptics TouchPad" with your actual device name from xinput

---

