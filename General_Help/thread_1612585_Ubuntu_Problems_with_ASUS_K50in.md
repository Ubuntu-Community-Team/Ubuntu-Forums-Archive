---
title: "Ubuntu Problems with ASUS K50in"
date: 2010-11-03
forum: General Help
---

### Post by Mizunga on 2010-11-03
Hellow everybody!!!

I'm new in Ubuntu, (and Linux), just installed it (Ubuntu 10.10) in my new netbook becouse i need security (is for university) and don´t like W7, and also when i installed it, I love the user interface, easy and fast.

The model is ASUS K50in, and i'm having some problems:

The list of Problems:

- Some of the icons dissapear or look bad (like 4 areas of Work or the Deskop icon).
- Sometimes i loose my Wifi connection and can´t find more, then i need to restart.
- When the screen saver start some times i can´t access again, and i have to shut down the computer.
- Reading CD sometimes the OS don´t read it, other times i can´t eject the CD, and have to restart 2 times (becouse first time don´let me join to any interface), start with Windows and Eject it on Windows. (I got a partition)

In other forum I ask for the same question, one user tell me maybe must be the mother board driver, but i can´t find the driver or maybe must be other thing... just i don´t know.

Any idea or suggestion please?

PD: Sorry for my english.

Regards!!!

---

### Post by P4man on 2010-11-03
Sounds like a terrible machine to run ubuntu on :S since these all seem unrelated problems to me.

One by one.

The icons that look wrong and disappear, I will need more info because Im not sure whats going on. Is it entire panels disspearing or not? Whats wrong with the icons? Can you make a screenshot when it happens?

For the wifi, we will need to know what wifi card you have. please open a terminal (applications > accessories > terminal) and type in the following commands:

```
lspci
```

```
lsusb
```

Copy paste the output here.

Screensaver, need more info too. What exactly happens? Doesnt the "unlock" screen appear, cant you type the password or what?

The CD I have heard that one before, and all I remember is that it was tricky to fix. Something about upgrading the firmware of the drive and/or disabling ACHI in the bios.

---

