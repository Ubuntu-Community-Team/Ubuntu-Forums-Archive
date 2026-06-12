---
title: "zSnes crashes on startup, help?"
date: 2009-07-26
forum: General Help
---

### Post by tega2919 on 2009-07-26
I tried to adjust the resolution to better fit my computer, but I guess it was a bad resolution, and now zsnes won't start up!

I tried running it under terminal and this came up: 


ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check [http://www.zsnes.com/](http://www.zsnes.com/) for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 3 mice detected.
Using ManyMouse for:
Mouse 0: Logitech Logitech USB Keyboard
Mouse 1: HID 062a:0000
get fences failed: -1
param: 6, val: 0
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  129 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x97
  Serial number of failed request:  125
  Current serial number in output stream:  127






I think the problem is with "X Error of failed request:  BadValue (integer parameter out of range for operation)"

How can I fix this?
I installed it using sudo apt-get install zsnes, and I am running Jaunty.
I tried uninstalling it using sudo-apt get remove, add/remove programs, and synaptic package manager. After re-installing it, the same thing still happened.
Help!










EDIT: Oh yes, I almost forgot.


ZOMG FIRST POST EVAR1!!!!11!!!11



EDITX2: I fixed it.

I ran zsnes -? and found the command -v which let me change the video resolution from the terminal.


WOOOOOOO

---

### Post by Yellow Pasque on 2009-07-26
There's also a configuration file you can edit, probably ~/.zsnes/zsnesl.cfg

---

