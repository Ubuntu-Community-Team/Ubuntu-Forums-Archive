---
title: "Kernel Panic after /sbin/init not found"
date: 2006-03-18
forum: General Help
---

### Post by ajmacca on 2006-03-18
Hi, first of all, I apologies if this has been answered already, or I'm in the wrong part of the forum, I'm new to these parts.  I have searched the forums and the closest thing I've found gives a slightly different error message and doesn't look like the same problem.

As background I'm running a dual boot with XP Pro and 5.10 Breezy (2.6.12-10-386 kernel).  I have windows on my first SATA drive and then Grub and everything related to Linux on my second SATA drive.  sdb1 is my boot partition, sdb2 is my swap, sdb3 is root and sdb4 is being used to try building linux from scratch.  My BIOS is set to boot to my second SATA drive, which loads grub, which then used to load Breezy.  Last night I was in Breezy, then suddenly it seemed as if anything that wasn't already loaded in RAM couldn't be accessed.  Whenever I tried to launch an application, it said the target executable couldn't be found.  I may have updated something just before this happened, but it was past 1 in the morning and I was not really paying attention to what I was doing (stupid me, I know).  I then restarted the system, which now begins booting Breezy, but eventually gives the following error:

[INDENT]run-init: /sbin/init: No such file or directory
[4294678.760000] Kernel panic - not syncing: Attempted to kill init!
[4294678.760000][/INDENT]

After this it just sits there waiting.  Unfortunately I recently got rid of my previous kernel as everything seemed fine with the new one.  I'm fairly sure I'd booted into the new kernel at least once or twice without the old one being there.  As I can't boot to a previous kernel I've tried launching the install DVD with 'rescue' but it fails to mount the root partition when I choose it (/dev/sdb3).  I've also tried launching the live DVD, opening a terminal, mounting my root partition, then chrooting into the root partition.  That also doesn't work, saying:

[INDENT]chroot: cannot run command `/bin/bash': No such file or directory[/INDENT]

I know for a fact that /bin/bash is there, as I can still read and write to the partition.  I don't know a whole lot about the booting process, but I think that my system might be getting confused as to where the root partition is.  As a result I've tried swapping the drive designations around in /boot/grub/device.map, but this didn't help either.  I'm at a complete loss as to how to solve this.  Obviously I can back up and start again, but I'd prefer not to if there's a solution to this problem.  I'm fairly busy with uni at the moment, but I should be checking back at least daily, and I'm happy to try any suggestions, or provide further information if anyone needs it.

---

### Post by ajmacca on 2006-03-22
I gave up on the problem and have since tried my hand at installing Gentoo.  For anyone that's interested, someone on a different forum said that my initrd image was probably stuffed.   The proposed solution was to compile my own kernel using a livecd, making sure to enable options for the root partition's fs.  This would mean  that the initrd image wouldn't be necessary, thus avoiding the problem.  Obviously the appropriate entries would have to be made in the bootloader configuration file.

Anyways, anyone watching this can consider the case closed!

---

### Post by smo0th on 2008-05-19
I have the same problem, shame you gave up, I'll just keep trying, if I get something I'll post it here.

---

### Post by ajmacca on 2008-05-19
As you can see it's been a while since I posted that.  From memory someone on a different forum thought that my kernel/initrd image was corrupt.  The suggested solution was to build my own kernel and edit my bootloader configuration accordingly.  At this point I decided to try a different distro and moved to Gentoo for a while.

Long story short, if you're up to compiling your own kernel and want to avoid a full re-install, give that a go.  Worst case scenario is you'll learn how to compile your own kernel if you don't already.

Sorry I can't be any more help.

---

