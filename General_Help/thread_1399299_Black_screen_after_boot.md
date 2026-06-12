---
title: "Black screen after boot"
date: 2010-02-05
forum: General Help
---

### Post by Macamba on 2010-02-05
Hi,

The other day I had some tiny problems with a root system that went foul. That was solved after a re-install (that seemed the fastest manner). Everything seemed to be running again. But today when I booted I saw the boot animation (the orange progress bar), and when it was time to show the log-in screen I got a black screen. 

This might have been caused by some propriety software I use for my system (ATI Radeon X1200 Series on a AMD Athlon 64 X2 Dual system). The software was suggested when I updated my Linux system from the LiveSystem CD I installed to the current flavour.  

Anyway, I have a black screen, on which I can enter my username and password, and log in. But as the screen stays black, nothing else can be done. Or can it?

Anyone know how I can solve this?

Macamba

---

### Post by lidex on 2010-02-05
Boot into a live session (CD) or into recovery mode from grub (hold down the shift key after bios screen if not displaying). Get to a command prompt and enter this command:
```
sudo apt-get install --reinstall gdm && sudo dpkg-reconfigure gdm
```

---

### Post by Macamba on 2010-02-06
Sudo it will be, thanks. :p

---

