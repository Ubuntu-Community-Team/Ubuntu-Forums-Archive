---
title: "Numlock?"
date: 2009-09-21
forum: General Help
---

### Post by TarasIv on 2009-09-21
I have a pretty generic Logitech keyboard, but the only time Linux lets me use Numlock is when using the calculator? Is there any way to enable it to let me use it anywhere throughout the OS? Thanks in advance! :)

---

### Post by ajgreeny on 2009-09-21
I have not needed it for several versions of ubuntu, but try installing **numlockx** from the repos.
Also try using gconf-editor - Desktop - Gnome - Peripherals - host-hostname - 0 and select what you want in that.

---

### Post by TarasIv on 2009-09-21
Thanks for the reply, will try. :D

EDIT: numlockx not working, but could you give a tutorial on the second option you mentioned since I am new to Ubuntu :D
         ....or does numlockx require a reboot?

---

### Post by ajgreeny on 2009-09-22
In the Alt+F2 dialog box type gconf-editor and burrow down as I showed Desktop -> Gnome -> Peripherals -> host-hostname -> 0 and there you will see a small select box, which is pretty self explanatory.  Select it and you should be OK.

I have not actually needed to use this however, as gnome seems to set the numlock to whatever state it was when you shutdown, or that's my experience, but having a full size keyboard, I never have numlock off, so can't really help with that any further.

---

### Post by TarasIv on 2009-09-27
Thank you so much!!!

---

### Post by prabhakar2 on 2010-04-17
thank you

---

### Post by Foxblood on 2010-04-24
Thank you very much.

---

### Post by MestreLion on 2011-02-17
Nice hint! Thank you VERY much!

Questions:

- Is this gconf method system-wide? I mean, does it turn numlock on even at login screen?

- What is the difference between this and "**Menu -> Preferences -> Keyboard -> Layout -> Options > Miscellaneous compatibility options -> Default numeric keypad keys**" ?

- Is there any way to tell Ubuntu to follow/respect/use the BIOS num lock setting ?

- How can i make it turn OFF when computer is SHUT DOWN ? In my PS/2 keyboard, it remains ON

---

