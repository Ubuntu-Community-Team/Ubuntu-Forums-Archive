---
title: "Monitor and lucid update wreaking havoc on system"
date: 2010-05-27
forum: General Help
---

### Post by wildman will22 on 2010-05-27
I got a new monitor for christmas this year and just reinstalled ubuntu (jaunty) not too long ago, like about a month. I finally got around to updating about two or three weeks ago to lucid. Now my monitor and lucid are fighting like some crazed technological married couple.

Basically, when I boot, a screen resembling kernel panic comes up for a while, and then normal boot resumes. A box comes up and says "monitor config file is either blank or contained only whitespace". If my computer limps itself along to the desktop, I find that my resolution is stuck on 1900x1080 and the icons that usually exist on my top panel are either gone or moved to the right. Under Preferences > Monitors it says unknown for my monitor, I only have the 1900x1080 option for res and my refresh rate says zero hertz.

Beyond that, my computer seems to enjoy randomly rebooting itself (sometimes even before it reaches the boot options screen) and my monitor has strange streaks/dots running up, down and across it that change when I hit keys or move the mouse, even without changing anything on screen.

I know that that's alot of info to sort through but I've tried all sorts of things far and wide trying to fix this. Including screwing with xorg.conf and trying to install the ATI proprietary drivers. (I gave up on the drivers, not being able to convert them to .deb) Thanks in advance for any help.

---

### Post by Naitsirhc Hsem on 2010-05-27
amd proprietary drivers can be executed in the terminal such as


```

cd Directory where downloaded driver is, usually Downloads
sudo sh amd2384-58324...whatever.bin

eg..

cd Downloads
sudo sh amd1.5.23_ProprietaryDriver.bin

```

or just go to System>Administration>Hardware Drivers (Works sometimes)

---

### Post by wildman will22 on 2010-05-28
Stupid me. I was downloading the rpm instead of the bin/run for the driver. Getting the bin now, I'll see if it helps at all.

---

### Post by wildman will22 on 2010-05-28
This is what happens when I try to install using the .run file.

```
aniel@HARVEY:~/Download$ sudo sh ati-driver-installer-8.28.8.run
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
Detected configuration:
Architecture: i686 (32-bit)
X Server: unable to detect
Removing temporary directory: fglrx-install
daniel@HARVEY:~/Download$ 

```

---

### Post by alphacrucis2 on 2010-05-29
> **wildman will22 said:**
> This is what happens when I try to install using the .run file.

```
aniel@HARVEY:~/Download$ sudo sh ati-driver-installer-8.28.8.run
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
Detected configuration:
Architecture: i686 (32-bit)
X Server: unable to detect
Removing temporary directory: fglrx-install
daniel@HARVEY:~/Download$ 

```

Which card have you got? Catalyst drivers older than 10.4 don't work with Lucid's xorg.

---

### Post by wildman will22 on 2010-06-02
My card is a radeon 9200. I installed the fglrx driver and that seems to have fixed the problem. Still getting the lines across my monitor and random shutdowns though, once didn't even make it past the bios screen. But I think xorg is working fine now, the lines are coming from somewhere else, possibly hardware related.

---

