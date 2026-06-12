---
title: "Need memory guru: massive swappage"
date: 2010-06-16
forum: General Help
---

### Post by Rocket J Squirrel on 2010-06-16
Karmic on netbook with 1GB ram.

I could use a little help identifying the cause of a massive swap that occurs several times a day. The computer will be running quite fine for a few hours, then it starts to pack up with endless swapping (as indicated by HDD lamp), and app screen going dark. Outwaiting it does not help, but closing an app, like Mozilla Thunderbird, or Google Chrome, or Mozilla Firefox, clears up the problem. I can then re-launch the closed app and the machine will be fine for a few more hours. Wash, rinse, repeat. 

I have looked at top to see if I can figure out who is doing the swapping but there's not much there I can figure out. System Monitor does not show anything major going on. 

Maybe someone could give me some things to look at and I can post what I see?

---

### Post by K.J. on 2010-06-16
> **Rocket J Squirrel said:**
> Karmic on netbook with 1GB ram.

I could use a little help identifying the cause of a massive swap that occurs several times a day. The computer will be running quite fine for a few hours, then it starts to pack up with endless swapping (as indicated by HDD lamp), and app screen going dark. Outwaiting it does not help, but closing an app, like Mozilla Thunderbird, or Google Chrome, or Mozilla Firefox, clears up the problem. I can then re-launch the closed app and the machine will be fine for a few more hours. Wash, rinse, repeat. 

I have looked at top to see if I can figure out who is doing the swapping but there's not much there I can figure out. System Monitor does not show anything major going on. 

Maybe someone could give me some things to look at and I can post what I see?

It's not necessarily swapping. I have a netbook (eee pc 901) and I used to get this. What resolved the issue was moving the home directory to a second drive since it gets written to frequently.

---

### Post by Yarui on 2010-06-16
Does this happen regardless of what programs you are running?  If the problem is resolved when you close all your opened programs I would guess that one of those opened programs just has a bug that is causing this to happen.  Monitor this activity while running a single one of those applications at a time and see if it still happens.  If you can find which program, or possibly combination of programs, is causing this you should try asking on forums dedicated to that program.  If you are lucky it may be a common bug that is already being patched.

---

### Post by dino99 on 2010-06-16
only install and use what you need, clean the system with gconf-cleaner and bleachbit

you can reconfigure those packages (firefox, gnome, ...) with:

sudo dpkg-reconfigure realpackagenameused

---

### Post by K.J. on 2010-06-16
Check system monitor for memory usage. Is there definitely a lot of swapping going on or is the drive just being written to a lot?

---

### Post by dapperdanny77 on 2010-06-16
top is a good tool for a first impression what's going on on your system.
just type top in the command line. by typing shift+m the process list is sorted by memory consumption

---

