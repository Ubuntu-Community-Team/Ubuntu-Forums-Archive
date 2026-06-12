---
title: "Mupen64plus input Configuration"
date: 2011-05-13
forum: General Help
---

### Post by Alan502 on 2011-05-13
Hi,

I updated my ubuntu recently but I found out that mupen64plus does not longer include a GUI. I have tried to configure my joystick with the instructions on their [website]("http://code.google.com/p/mupen64plus/wiki/ControllerSetup") but I didn't have an InputAutoCfg.ini file, although I created it and put the text in it but it still doesn't work?? Can someone help me?

Edit: I tried cutemupen but it says "invalid resolution"

---

### Post by Surkow on 2011-05-13
I would recommend visiting their IRC channel. Run "mupen64plus --saveoptions" to save the current configuration to a new configuration file called "mupen64plus.cfg" (found at "~/.config/mupen64plus/"). You can configure your joystick there.

---

### Post by Alan502 on 2011-05-13
I visited their IRC channel #mupen64plus@freenode, and they helped me to configure my joystick. You have to follow the instructions here: 

[http://code.google.com/p/mupen64plus/wiki/ControllerSetup](http://code.google.com/p/mupen64plus/wiki/ControllerSetup)

but the InputAutoCfg.ini file that the document talks about is actually on **/usr/share/games/mupen64plus** on ubuntu

---

### Post by Surkow on 2011-05-14
That's only necessary when you want your joystick to be configured automatically. That file contains all input devices that will be automatically detected. It's much more logical to edit the "mupen64plus.cfg" configuration file. With each update your InputAutoCfg.ini can be overwritten. If your device is not among the auto configured devices you can send your input configuration to the mailing list.

---

