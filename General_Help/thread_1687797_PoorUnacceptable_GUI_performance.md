---
title: "Poor/Unacceptable GUI performance"
date: 2011-02-14
forum: General Help
---

### Post by Lead Head on 2011-02-14
I've done tons of search yet have found nothing conclusive. The GUI performance in 10.10 on this computer is horrible. The mouse moves around jerkily, when you drag a window around it feels like it is about at about 5 FPS, it is just really not usable at all.

It is only the GUI however. Flash videos play smoothly, I can play 3D Games like Counter-Strike through Wine without issue, etc..

The system is an AMD Opteron 165 Dual Core @ 2.7GHz, 1.5GB RAM, and an ATI Radeon HD4770 video card. I do have the ATI/AMD proprietary drivers installed, but if I un-install the drivers and reboot, the GUI performance at the welcome screen is great until I log in, then it immediately goes back to poor performance - even with the proprietary drivers un-installed.

It definitely seems to be an issue with X, because if I enter "top" in the terminal and watch the CPU usage, if I start to move a window around rapidly, X CPU usage shoots up to around 30-40%, and I have all the graphical effects disabled right now.

---

### Post by Lead Head on 2011-02-14
Anyone have any clue at all?

---

### Post by coffeecat on 2011-02-14
The proprietary driver may be the problem. In theory the open source driver *should* give perfectly good performance with the HD4*** series - it does with my HD4350. Sometimes, though, the proprietary driver doesn't uninstall properly, leaving bits of itself behind, causing problems. Have a look here:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

I suggest you go with the aggressive "Need to fully remove -fglrx and reinstall -ati from scratch" option and see whether a system properly purged of the fglrx driver works better for you.

---

### Post by uRock on 2011-02-14
> **Lead Head said:**
> Anyone have any clue at all?
Please wait 24 hours before bumping.

Thanks,
uRock

---

### Post by Lead Head on 2011-02-14
Well that full system purged worked even after I logged in. As soon as I clicked on Firefox, X broke itself instantly somehow again, and now it is back to the way it was.

This is getting beyond ridiculous.

---

### Post by uRock on 2011-02-14
Did you just install or did an update cause this?

Do you have this issue when running from a 10.10 LiveCD?

---

### Post by Lead Head on 2011-02-14
Fresh install. I haven't tried the LiveCD, but the installer had the same poor performance.

---

### Post by Lead Head on 2011-02-14
I really wish I knew why,but it seems purging Ubuntu One solved my problems.

I tried re-installing the ATI Proprietary drivers, but X once again started doing the same thing. The killer is that the drivers work, I get over 9000 FPS in glxgears for example, but X performance is just terrible. 

For whatever reason, it seems that Ubuntu One and the ATI Drivers make X flip out.

---

### Post by Lead Head on 2011-02-14
Welp, I'm done with Ubuntu until the next release. Given completely up on 10.10. Ran the same exact purge commands in the same exact order as I did early, went to restart, never booted back up again. Splash screen shows up, then the monitor turns off and that's it.

Back to Windows - again.

---

### Post by matt_symes on 2011-02-14
Hi

> Back to Windows - again.

You could always try a different Linux distro (Fedora, OpenSusi, ...)

Kind regards

---

### Post by uRock on 2011-02-14
> **Lead Head said:**
> Fresh install. I haven't tried the LiveCD, but the installer had the same poor performance.
This tells me that something may have been wrong with the CD itself. Did you run the disk check before installing?

I always test the newer version before installing and I always test the disk before doing anything else with it.

---

### Post by Lead Head on 2011-02-14
It was a USB drive install. This is not the first time I've had this issue. I tried 10.10 a few months ago with a Live-CD install, tried 10.04 - same issue.

Tried Fedora, same issue again. 

I've basically given up trying to get Linux to work right with this computer. The last Ubuntu distro I had working good on this computer was 8.10, and that was years ago.

---

