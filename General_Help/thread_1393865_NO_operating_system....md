---
title: "NO operating system...???"
date: 2010-01-29
forum: General Help
---

### Post by robertcoulson on 2010-01-29
Hi...
Don't know if it is possible...I have an old laptop that my son-in-law formated the hard drive...I tried to put Ubuntu on it, but it stops at "No operating system"...Am I beating a dead horse (so to speak), or is it a good boat anchor...??
Bob

---

### Post by SoFl W on 2010-01-29
> **robertcoulson said:**
> Hi...
Don't know if it is possible...I have an old laptop that my son-in-law formated the hard drive...I tried to put Ubuntu on it, but it stops at "No operating system"...Am I beating a dead horse (so to speak), or is it a good boat anchor...??
Bob

Are you able to boot from a CD and if so is the computer set up to boot from the CD first?

---

### Post by Megafag on 2010-01-29
> **robertcoulson said:**
> Hi...
Don't know if it is possible...I have an old laptop that my son-in-law formated the hard drive...I tried to put Ubuntu on it, but it stops at "No operating system"...Am I beating a dead horse (so to speak), or is it a good boat anchor...??
Bob

Look at the bios and make sure you have the correct device selected for first boot device.

---

### Post by robertcoulson on 2010-01-29
Yes, I have set it up to boot from CD first, but to no avail.
Bob

---

### Post by Megafag on 2010-01-29
> **robertcoulson said:**
> Yes, I have set it up to boot from CD first, but to no avail.
Bob

What laptop is it?
and how did he format the drive?

---

### Post by robertcoulson on 2010-01-29
It is an older Toshiba and I think he just " Fdisk"...If that sounds correct...???
Bob

---

### Post by Megafag on 2010-01-29
> **robertcoulson said:**
> It is an older Toshiba and I think he just " Fdisk"...If that sounds correct...???
Bob

ok well check the CD on another computer, try booting from USB maybe? but truth be told i really dont know :( . post back if you have any success

---

### Post by LuridCinema on 2010-01-29
I just did an install and the system would load SLOOOOW on the CD , so I used a USB install , it worked very well. mebbe it might work in your case if the laptop will allow USB boot

---

### Post by robertcoulson on 2010-01-29
Ya...Old computer with NO usb...Thanks for trying, appreciate it.
Bob

---

### Post by Sef on 2010-01-29
> Old computer

What are your system specs?   Ubuntu could be too slow, but there would be other distros that could work on your machine.

---

### Post by Shpongle on 2010-01-29
some of the old models require you press a key eg f2 f12 or f8 or something to load a boot menu ,otherwise they default to hdd

---

### Post by robertcoulson on 2010-01-29
I have changed it to boot to CD first, but maybe you have something Sef, I could try another distro...Thanks
Bob

---

### Post by Megafag on 2010-01-29
> **DillByrne said:**
> some of the old models require you press a key eg f2 f12 or f8 or something to load a boot menu ,otherwise they default to hdd

This.

OP try holding the "C" key when the computer starts up. also if its so old that it has no USB it is quite possible ubuntu wont be the best idea. 

you could try crunchbang linux or maybe xubuntu?

---

### Post by robertcoulson on 2010-01-29
Ya...you guys maybe right, another lighter distro might work...Worth a try.
Bob

---

### Post by lisati on 2010-01-29
My old desktop boots from some CDs but not others. One option I sometimes find useful is a floppy with [smart boot manager]("http://sourceforge.net/projects/btmgr/") installed on it.

---

### Post by robertcoulson on 2010-01-29
Lisati...Do I run this before trying to install from CD...??
Bob

---

### Post by cptrohn on 2010-01-29
> **robertcoulson said:**
> Ya...you guys maybe right, another lighter distro might work...Worth a try.
Bob

You might try puppy linux 4.31.  It's great with older hardware.

[http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm)

---

### Post by egalvan on 2010-01-29
> **robertcoulson said:**
> Hi...
...I have an old laptop that my son-in-law formated the hard drive..., but it stops at "**No operating system**"...
Bob

"No Operating System" is BIOS-speak for 

"I checked the hard drive but couldn't find a valid boot"

which means that it has already skipped the CD drive...
which means it did not find a valid boot on the cd.

Which could mean defective CD drive, or defective/problematic CD.
(A CD burned too fast may be problematic on older optical drives.
The older lasers and collimaters cannot handle the reduced contrast in light/dark levels when cd's are burned at higher speeds.)


No USB probably means neither the CD drive nor the hard drive are easy to remove and install (to facilitate testing the hardware)

(An easy out is to remove the hard drive and do the install on another machine.)

Does it have a network connection? PXE is another possibility
Hardware or software PXE.

Does it have a floppy?
a Linux boot disk is another possibility.


and by the way,
How much RAM does that Pleistocene relic have :)

---

### Post by robertcoulson on 2010-01-31
Well...I could try Puppy Linux, but you may be right...The CD drive MIGHT be defective....NO USB for sure...so I will try another linux and see...Thanks
Bob

---

