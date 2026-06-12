---
title: "Double boot; seperate hard drives"
date: 2011-04-26
forum: General Help
---

### Post by HostPost on 2011-04-26
Hi,
I have seen a few dual boot topics in the forums that run two O/S's from the same drive.

What I am planning on doing and seeking advice on is having Win XP on one hard drive and Ubuntu running on another seperate H/D from within the same computer.

Has anyone done this before please? I am looking to see if there is a way to run a double boot that fires up both XP and Ubuntu so that the two drives can be switched to on the fly. 

Any thoughts please, or am I wishing for too much here?

regards
Dave

---

### Post by btindie on 2011-04-26
That's very straight forward and has been done for years.

The easiest way to do this is to make your Ubuntu hard drive your primary one so that the BIOS boots this one first. Install Ubuntu on that drive along with the boot manager Grub2, it'll automatically detect Windows and create the boot entries for both OS's. Simple.

---

### Post by Lateralis on 2011-04-26
Having Ubuntu and Windows on separate physical devices is perfectly fine.  At one stage I had a different Linux OS on one disc, Ubuntu on a second and Win XP on a third.  That got a bit messy, but was fine.  It may also even be preferable to have Ubuntu and Windows on separate discs, as the Windows drive will still retain its bootloader, with Grub installed by default on the Ubuntu disc.  Thus if something goes squiffy with Grub or Ubuntu, Windows will still boot up fine, so long as the BIOS is directed towards your Windows drive as the first boot device.  And Grub should pick up the other Windows disc just fine at install. 

As to whether it is possible to switch between Ubuntu and Windows essentially instantly without requiring a restart... I'm not sure that's possible.  The BIOS will seek to load up the bootloader on what you tell it is the first hard disk.  If that first HD contains grub then you will choose which OS to boot into.  What you may want to consider doing is using a virtual machine or Wine in Ubuntu if you want to use Windows software that isn't too intensive.  If you want to play games, then best stick with a dual boot and restart between the two OSs as necessary.

---

### Post by HostPost on 2011-04-26
Wow, thanks for the quick replies. Nice to know that running both is a simple process. I guess the switch over looks like another issue altogether. Yes I was hoping to avoid a restart to get to each OS.

Maybe that is not possible after all.

---

### Post by searchfgold6789 on 2011-04-26
Yeah, that would only be possible if you had two entirely separate PC's going to the same monitor. Then you could fire up both and use the keyboard to switch monitor inputs.

---

### Post by btindie on 2011-04-26
> **HostPost said:**
> Yes I was hoping to avoid a restart to get to each OS.
Is there something specific you need windows for? There are various options you can take to get around this.

[LIST=1]
[*]Find an alternative Linux application
[*]Run the Windows application under WINE on Linux
[*]Run Windows under KVM/VirtualBox on Linux
[/LIST]

---

### Post by Mark Phelps on 2011-04-26
> **HostPost said:**
> ... I am looking to see if there is a way to run a double boot that fires up both XP and Ubuntu so that the two drives can be switched to on the fly...

Regarding double-boot, the answer is NO.  Only one OS is booted at a time; you have to reboot to switch OSs.

If you want to explore the virtualization option previously mentioned, that DOES allow for both OSs to be running -- with one basically running inside the other -- but you have to partition off your memory to the individual OSs.  So, you need lots of memory and a reasonably powerful CPU to get good performance in both OSs.

And, BTW, if you decide to run Windows inside a virtual machine inside Ubuntu, you have to reinstall it from scratch -- to the virtual machine.

---

### Post by HostPost on 2011-04-26
Thanks for all the useful replies. 

Installing Windows from scratch isn't a problem since the hard drive has been knack'd by a file infecting virus and I need to do this anyway.

The PC that went down have several WIN accounts on it; family, personal and business. I am migrating all my business affairs off of the XP set up onto Linux to try and avoid any future Windows failures like that. I am cherry picking all the files and docs I need to keep.

I am running Linux from an older box running 100% Linux which is OK. I know I can run both and switch between the two with the same keyboard/mouse and have the tool to do that.

The old machine is on a Pentium 1400 processor with 1Gb of RAM and about at its limit. The new machine is a dual processor and has 4GB of RAM, so is a more attractive stronger PC to run everything from - hence my interest in the double booting question and keeping the Linux on another separate H/D.

Maybe running a virtual machine may be the answer but it seems that they both will still need to exist on the same drive.

Regards

---

