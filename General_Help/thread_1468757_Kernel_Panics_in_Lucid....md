---
title: "Kernel Panics in Lucid..."
date: 2010-05-01
forum: General Help
---

### Post by parm289 on 2010-05-01
I upgraded my Jaunty system to Lucid yesterday, and since the upgrade I've been getting constant, seemingly random kernel panics (the system freezes and the caps lock blinks).  I've looked at all the logs, and there is absolutely no info on anything that could be causing the panic. In fact, syslog and dmesg don't record anything at the time the system goes under, so I'm left guessing what the cause could be.

My main suspect was my NVIDIA graphics (GeForce 7600) and the use of nouveau, proprietary, or no driver.  I've tried the system with all 3 options, and I still get the panics, so seems that there's no dice here.

Next I played around with my wireless.  I use a Linksys USB adapter, WUSB54G version 2.  This worked OOB in Jaunty, but did not in Lucid.  So, I downloaded ndiswrapper from their sourceforge page and loaded up my windows drivers.  The system panics whether or not ndiswrapper is loaded.

Next, I worked on my cdrom drive...and I got panics whether or not there was a cd present.

I haven't played with sound, but that doesn't seem to be the problem because I don't get any errors associated with my sound card, and panics happen even when no sound is playing.

The one recurring error that I get in syslog is ```
matt-desktop-ubuntu kernel: [ 1006.387965] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
May  1 16:56:23 matt-desktop-ubuntu kernel: [ 1006.387970] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
```
This is an error with my microsoft wireless keyboard, and I've tried the terminal command it suggests: ```
setkeycodes e059 255
```, to no avail.

I was hoping to get some help here, but I realize it's hard to help without any info...I can post my logs if needed.  My hardware is:

-Core2Duo 1.86 GHz
-Asus p5nsli motherboard
-Marvell Yukon LAN (i can get the model no.)
-? Sound card - I get get model no. if needed

Thanks in advance.

---

### Post by clhsharky on 2010-05-01
HI parm289

How did you update from Jaunty to Lucid?

Sharky

---

### Post by parm289 on 2010-05-01
> **clhsharky said:**
> HI parm289

How did you update from Jaunty to Lucid?

Sharky

Clean install.  Unfortunately, because I did a clean install, there are no previous kernels to fall back to...

---

### Post by parm289 on 2010-05-01
I've reinstalled three times now, and the problem still persists.  I've looked in the bios for settings to change, and the only setting worth changing was turning off my nonexistant floppy drive (which did allow me to boot directly into the installer, whereas before the installer failed and I had to start it from the live desktop).

The panics continue to happen at random times, whether I'm connected to the Internet or not connected, playing sound or not, using nouveau graphics or not, using apt or not, using the cd drive or not, etc.  There seems to be no common theme to the panics, especially since no info about the panics gets recorded in the logs.  The only indication I get of a panic is the total freeze and caps lock flashing.

Ubuntu has never given me such trouble before - only with lucid.  I'm ready to give up and move back to jaunty if there are no solutions...

---

### Post by parm289 on 2010-05-02
Ok.  Without discovering what caused the random panics, I've solved the problem by moving to a 64-bit install.  I reinstalled 10.04 64-bit over my 32-bit install, and have been up and running for about an hour no with no panics.

---

