---
title: "Messed it all up, Need IMMEDIATE help!"
date: 2009-10-06
forum: General Help
---

### Post by FuzzyAdam on 2009-10-06
I have just got ubuntu 9.04 today for the first time. I tried putting effects on using compiz. But something went wrong. Now every time i turn on the computer and move the mouse over an icon or open a window it just goes black and I cant see the window or icon to use it. Is there a way I can start up without effects on to turn them off? Please help me!

---

### Post by beesthorpe on 2009-10-06
you could reboot in recovery mode and turn compiz off.  Just hit "Esc" at the grub screen and you'll get an option screen which includes recovery mode.

---

### Post by FuzzyAdam on 2009-10-06
Sorry im a bit of a noob, whats the grub screen?

---

### Post by beesthorpe on 2009-10-06
Okay - when you reboot the machine first you'll get some sort of message screen from the bios then you'll get a black screen that says something like "GRUB loading stage 1.5"  at the top. Hit the "esc" button at this point and you'll get an option screen. Choose one that says "recovery mode", hit enter and hope for the best :)

---

### Post by FuzzyAdam on 2009-10-06
Okay, I done that, i got a screen with a few options and at the endof 2 of them it said (recovery mode). I tried both, i got a blue screen with a load of options one if which was to do with graphics, i done that, it didnt work, ive tried it a few times but it didnt do anything. What am I doing wrong? Will I have to completly re-install ubuntu? :( Im not off to a good start with it.

---

### Post by beesthorpe on 2009-10-06
Oh dear - what I was expecting is that you could use the "xfix" option or to overwrite your config with a generic setup.  Have you tried simply turning compiz off by going to   "System > Preferences >  Appearence"   then selecting the "visual effects" tab in the dialogue box and setting it to "none"

---

### Post by CatKiller on 2009-10-06
One way to do it - not necessarily the best, but certainly one that will work - is to switch to a virtual console instead of logging in to the graphical environment with Ctrl-Alt-F1. Log in there, which will take you to a command-line based environment. Then use ```
nano .gconf/desktop/gnome/applications/window_manager/%gconf.xml
``` to open the GConf key for editing that controls the window manager.

(you can use Tab-completion to make this easier - type nano .gconf/d<*TAB*>g<*TAB*>ap<*TAB*>w<*TAB*><*TAB*>)

Change both the stringvalue entries (current and default) from whatever they are to */usr/bin/metacity*. Ctrl-O saves and Ctrl-X exits.

Switch back to your graphical environment with Alt-F7 and then log in. You should then be running without desktop effects while you correct whatever you did.

---

