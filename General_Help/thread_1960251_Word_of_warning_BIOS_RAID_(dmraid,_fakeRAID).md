---
title: "Word of warning: BIOS RAID (dmraid, fakeRAID)"
date: 2012-04-17
forum: General Help
---

### Post by ladasky on 2012-04-17
Hi folks,

Many of you read (at least part of) my long rant about _[losing a working RAID1 setup using the motherboard's BIOS RAID, on a dual-boot Oneiric / Vista system]("http://ubuntuforums.org/showthread.php?t=1958874")_.  No one seemed to have any advice for me.  Before I go and start a new, more succinct thread, with just a question -- let me share what I think I have learned, following a recent system crash.  Maybe it will help some of you avoid problems.

On some motherboards for AMD CPUs, ones which use a 600 or 700 series South Bridge, the BIOS-based RAID (to which Linux interfaces through dmraid) can apparently fail, **irreversibly**.  When this happens, the problem is likely not the disk drives in the RAID, but rather the RAID controller itself.  _[Read here]("http://tecnicambalandia.blogspot.com/2011/11/amd-sb600-sb700-raid.html")_:

> With SB700 based RAID 1 has some quirks, as does SATA in general on these SB700 (SB600 too) based boards. I've been through 4 different Gigabyte 780G boards, ALL had RAID 1 problems of some sort. More often than not, the drives are FINE!!!! (I don't know in your case).
 
It seems that what happens is that the SATA/SB/RAID controller thingy (not sure which exact piece of logic) loses its marbles, and cannot understand what is going on with the RAID set. It could be the driver also, but I don't think so. I believe it is an inconsistency in the SB silicon unfortunately. It could be firmware too (DFI has been one of the few who has been furiously putting our AMD RAID BIOS updates for the past year, but no one else seems to care)...
 
When the thing refuses to rebuild, unfortunately, it may be the SB700 lobotomizing itself finally. I've had the same thing on SB600 based boards (the Asus M2A-VM is famous for puking its RAID volumes.)

My system worked for months.  When it crashed, the two operating systems REFUSED to negotiate a reconnection to the BIOS RAID.  The strange thing is that the data on both drives seemed to be perfectly intact, and up-to-date.  I backed up my data to an external drive, from both Vista and Linux, without trouble.  But the system will not let me reconstruct a RAID using the BIOS -- even if the RAID is empty.  I'm not even trying to ask it to rebuild a mirror.

Linux has mdadm, of course, and before I switched to a dual-boot system I was using mdadm without trouble.  I'm thinking of going back to mdadm.  Of course, that leaves open the question of how to mirror my Vista partition... if it weren't for income tax preparation software, I could dump Windows.

---

### Post by ladasky on 2012-04-17
One bump for the daytime readers...

---

### Post by carreira on 2012-04-17
I never used fakeraid before, because of several problems I wish to avoid. I use linux software raid (mdadm) in my computer and although sometimes I need to use windows, I don't have a dual boot linux/windows.
My preference is to use virtualbox to run windows as a guest system to do some work I need.
Virtualization could be a solution for you if your computer is able to do it (cpu/memory).

---

### Post by ladasky on 2012-04-17
Thanks for your reply, carreira.

I have just a few Windows applications that I need to run.  Of course, they will not run under Wine.  I wasn't aware of VirtualBox.  How much of a performance penalty is typical under virtualization?  As with Wine, do I need to be concerned that some applications might not run?

My system is reasonably powerful, a AMD Phenom II X6 1090T CPU, 4GB of RAM.  It is supposed to be able to accept 8GB (though the extra RAM that I tried plugging in last week had trouble, I probably have to tweak the motherboard settings).

---

### Post by carreira on 2012-04-17
This is powerfull enough to not feel a significant performance penalty.

> As with Wine, do I need to be concerned that some applications might not run?
Probably no!
I only had some problems with a software named Nokia PC Suite that manages the phone over a usb cable. Generally usb cables don't have issues under virtualbox, but this kind of software is very demanding with usb connectivity.
I think you will be happy with the results! Try it!
You can also try KVM as an alternative to Virtualbox (but I'm not experienced with it).

---

