---
title: "can I install mac software on ubuntu??"
date: 2010-12-21
forum: General Help
---

### Post by kinderen on 2010-12-21
i have used wine for a long time but with more then half of the programs I install there is allways something that does not work or it does not work at all. so i was wondering if i could install mac software. if i could it might run better then the windows software.

thanks
vince...

---

### Post by oldsoundguy on 2010-12-21
In a nutshell, I believe that the answer is a big NO.
Apple software is hardware dependent.

You have choices.  
One is to blow off Wine and MS programs all together.
Go looking for Linux substitutes and install those.
Or run your "I just gotta have this Windows program" out of a VM with Windows installed or separate partition with Windows.
Or a separate computer with Windows and your got to have programs.  Run that through a physical KVM switch and you can move from one to the other without re-booting or jumping through hoops.
You can even network them and allow file sharing.
(the latter is what I have done in order to have unrestricted access to my photography/music/PDA programs.)

---

### Post by ninjaaron on 2010-12-21
As far as the little bit I've looked into it, the answer is "no, not at all," but perhaps someone knows better than me.


Linux software, on the other hand, usually installs just fine. ;) (Seriously though, if there is something you really need, you can usually find a good open source replacement. I realise there are exceptions to this, but normally it's just a matter of learning the new software. Now that I'm adjusted to my Linux software, I feel much more limited when using other work environments. Not trying to be a jackass. Just a thought.)

[edit]
Ah, right. forgot about dual-booting, VM's, etc. That tends to work pretty well for a lot of people. I recently deleted my windows partition because I didn't have anymore use for it, now that flash pretty much works on Ubuntu (youtube always worked, but Mega Video and some others were problematic. Work fine now, though it is greedier for resources than in Windows and OSX). I had OSX a long time ago, but I ditched that too. I'm actually writing on my ubuntu MacBook right now.

---

### Post by kgarbutt on 2010-12-21
There are three main emulators:

Basilisk II can handle m68k mac emulation. It can not run PowerPC binaries, and supports MacOS 7.0 -> 8.5 IIRC. It has a just-in-time recompiler and is quite zippy. Basilisk requires a ROM image, but ROMs for m68k macs are easy to find. Of course, legally you must own the mac anyway.

SheepShaver is a PPC emulator mostly for old-world PCI macs, and handles MacOS 7 and 8, including PowerPC binaries. Like Basilisk (which it shares a lot of code with) it has a JIT recompiler. SheepShaver requires a ROM image, and ROM images for old-world PCI PowerPC macs are (almost?) impossible to find. Legally you must own the mac anyway.

PearPC is an emulator for New World Open Firmware based macs and supports MacOS X, but not MacOS 9 or MacOS/X's "Classic" mode. It also now has a JIT recompiler, but I don't know how well it performs. I don't know what the ROM and licensing situation is with PearPC.

---

