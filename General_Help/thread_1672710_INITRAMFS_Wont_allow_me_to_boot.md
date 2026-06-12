---
title: "INITRAMFS? Wont allow me to boot?"
date: 2011-01-21
forum: General Help
---

### Post by ZeroRider13 on 2011-01-21
Hey, I am booting from my hard drive, but I get a long list of code and everything and at the bottom is:

type "help" for more information
<initramfs>

Im not sure how to fix thing...nothing has changed, nothing has been installed, I just want to boot up like always and this screen just wont allow it.  I am currently using a live version from a USB stick.  Please help me out.  THanks

---

### Post by Hippytaff on 2011-01-21
Can you post the results.txt gerenarted by downloading and running [this bootscript]("http://sourceforge.net/projects/bootinfoscript/")

---

### Post by ZeroRider13 on 2011-01-22
above that it says init not found or something also, I just dont see what happened between last night and now.  Also, I'm sorry but I don't know exactly how to do that.  =/

---

### Post by satyanash on 2011-01-22
Here is how to generate the results.txt hippytaff is talking about.
Follow the instructions::

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Satyajeet

---

### Post by ZeroRider13 on 2011-01-22
Alright thank you, it seems to be stuck on 

Searching sdal for information...

if this is the usual, I'll wait but it really seems stuck.  Thanks again.

---

### Post by Hippytaff on 2011-01-22
It shouldn't hang if you boot from liveCD/USB

---

### Post by satyanash on 2011-01-23
I think he means the script hangs at the point and not the booting process..:popcorn:

---

### Post by tk189 on 2011-01-23
Does the error say something like

No init found try passing bootarg


If so this has cropped up all over the place and affected alot of people.

The only thing I found that worked was to follow drs305's walkthrough to [purge and re-install the grub ]("http://ubuntuforums.org/showthread.php?t=1581099")bootloader

You have to boot a liveCD (USB) session then use the chroot command to get into the actual harddrive installation otherwise you'll just be trying to purge and update the liveCd bootloader which won't help.

The walkthrough is very thorough but I found I had to do it daily.

More recently it has been noticerd via the massive thread on this forum about random freezes and crashes that CPU fan setting (in bios) and even the use of compiz visual effects can be causing strange behaviours.

Since disabling visual effects and setting my CPU fan differently I haven't had a single crash, freeze or boot error.

Check out the walkthrough: [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

