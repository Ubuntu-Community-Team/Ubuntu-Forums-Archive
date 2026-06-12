---
title: "Start Up Problems with 9.10"
date: 2010-02-07
forum: General Help
---

### Post by gryffinwings on 2010-02-07
I'm having a problem with start up with Ubuntu 9.10, before it gets to the loading screen that is before the login screen, it goes to a black screen and does nothing, so far I'm at a loss as to what to do. My specs are as follows:

CPU: Pentium 4 - 1.7 GHz (Northwood Core)
Motherboard: Intel d845glva
Memory: 1 GB
Harddrive: 160 GB Western Digital
Power Supply: Antec Basiq Power 430 watt

I will be installing a PCI slot EVGA GeForce 8400 GS 512MB DDR2. Anyways I'm just trying to fix the problem, if possible please add instructions.

---

### Post by oshunluvr on 2010-02-07
First - check the md5 sum of the cd you have to make sure you've got a good burn.

Just to be clear - 

Graphics boot sequence for "Try Ubuntu without installing..."

First: Ubuntu logo in the center of the screen
Second (not always): Text console and messages of any errors
Third: "Ubuntu" with a spot light effect behind it
Fourth: Spinning cursor (Wait icon)
Fifth: Desktop 

After which step does the screen go blank?
Does Alt-F1 get you to a text console?
Is the keyboard active at all - try toggling caps lock or something with a LED response if you have one on your keyboard. If this fails, try holding down CRTL-ALT-SysRq-B and see if it reboots.

---

### Post by gryffinwings on 2010-02-07
> **oshunluvr said:**
> First - check the md5 sum of the cd you have to make sure you've got a good burn.

Before I did an install I did a check of the CD first and the onboard program confirmed that it was a good burn.

---

### Post by gryffinwings on 2010-02-08
Bump.... I'm still having problems with this.

---

### Post by HPD2 on 2010-02-08
You may have to edit the kernel line in your grub.cfg and append "nomodeset" to the end of it. I installed ubuntu on an old Dell Optiplex SX270 and the screen would go blank before it got to far in to the boot.

Load up the alt cd (dont know if the live will work) and go in to "recover broken system" then from there go through the steps till you get to a point ware it will ask you to mount your root file system. once mounted open a terminal then cd to /boot/grub and the file you want to edit is "grub.cfg"```
nano /boot/grub/grub.cfg
``` from # or ```
nano grub.cfg
``` after you cd to /boot/grub.
Hope that helps.

---

### Post by bindurkv on 2010-02-08
I too am having a start up problem with Ubuntu 9.1.  Till Login, no issue. But after that I am getting a screen which is not decipharable. :confused:

---

### Post by shimanoreels on 2010-02-08
hey.....! i am also facing the same problem.can suggest me some good advice's
[shimano reels]("http://www.shimanodiscounted.com/index.php?cPath=1&osCsid=91d72069a7798ad5341f4c5dbbcd5684/")

---

### Post by mörgæs on 2010-02-08
Ubuntu 9.10 has some known problems with logging in. Sometimes the easiest solution is installing 9.04.

[http://releases.ubuntu.com/9.04/](http://releases.ubuntu.com/9.04/)

9.04 is supported till October 2010.

---

