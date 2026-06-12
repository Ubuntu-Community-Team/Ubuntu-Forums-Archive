---
title: "Migrating / to new partition"
date: 2011-07-02
forum: General Help
---

### Post by RansomOttawa on 2011-07-02
Hi all.  I've tried searching for this question but found no answer that was reasonably current, nor seemed to fit my exact circumstances, so here goes.

I'm currently running Ubuntu 10.04 exclusively.  Until recently my system had / and /home on separate partitions on the same physical drive, but I've installed a new, larger drive and migrated /home completely over to it. This has freed up a whole bunch of space on the primary drive, which I'd like to repartition to accommodate a few other operating systems that I want to play around with (other Linux distros, and so forth).

This would also include reinstalling Windows XP.  Being Windows, it likes to be installed on the first primary partition on the first drive - exactly the position that Ubuntu is currently in.  I know that Linux really doesn't care where it's installed, so I'd like to know if it's an easy matter to migrate my Ubuntu install to another partition without rendering it unusable.

Based on my experience migrating non-root partitions in the past (e.g. /home), my educated guess is that the procedure should work something like this:

[list=1]
[*]Create a new, empty ext4 partition (say, /dev/sda2) alongside the existing one containing / (/dev/sda1)
[*]Copy sda1 --> sda2
[*]Update /etc/fstab with the new location for /
[*]Install Windows to sda1
[*]Boot to sda2 and restore grub
[/list]

I'm not going to rush right into this, of course. But is my thinking sound? Are there any obvious steps I've missed? Is there a recent howto of some kind that would address this accurately?

Many thanks!

---

### Post by hawthornso23 on 2011-07-02
Edit: - deleted previous comment - didn't read what you wrote carefully enough - thought you'd forgotten about fixing the MBR and restoring grub.

---

### Post by oldfred on 2011-07-02
While many say Windows has to the the first partition, it does not. It does seem to work better if it is the first drive sda, but that is not a requirement either.

You do have to have a primary partition sda1 thru sda4 formated to NTFS with the boot flag for Windows to install. Then you need to make the rest of the drive an extended partition so you can install many other partition.

I prefer to have all of one system on one drive so if one drive crashes, then I can boot the other. And I want the boot loader for that system in the MBR of the drive with the system. I now keep /home inside my / (root) partition and use NTFS /shared for any data I want in windows and other system like my Firefox & Thunderbird profiles and a /data partition for any data I want to share in my other systems. All systems may not share a data partition equally well as user numbers UID's may not be the same. But all of the installs I share currently are Debian based.

---

### Post by RansomOttawa on 2011-07-04
So if I understand you correctly, it is possible to install WinXP somewhere other than the first primary partition on the first physical drive - and that all I have to do is create a new primary partition on the drive (say, in the second position) and flag it bootable, and I should have no trouble with the install?

I don't want to sound skeptical, but I have had issues in the past with Windows being very crashy if it wasn't where it preferred to be, so I don't want to spend my time on a wild-goose chase.

---

### Post by oldfred on 2011-07-05
I have seem many boot script with windows in other places than sda1. Generally the instructions are to install windows first, then it is sda1. But there are instructions for installing second.

These are older, before grub2 so do not follow all the details:

Older but discusses the issues, reinstall grub2, not other alternatives:
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)
[https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu](https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu)

You will have to reinstall grub2's boot loader to the MBR of sda.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by RansomOttawa on 2011-07-05
Thank you for the links. I should be trying this later in the week, and I'll be sure to report in on what happens.

---

