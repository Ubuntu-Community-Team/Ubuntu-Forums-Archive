---
title: "how to remove kernels off non-main HDD in system"
date: 2012-01-31
forum: General Help
---

### Post by Robertjm on 2012-01-31
Hi all,

A couple of months ago I built a new computer and installed Precise Penguin 12.04 alpha 1 on it. When I built the system I used a SSD as my main drive, and then took the two IDE drives I had in my system and installed them as well, using IDE-to-SATA adapters to get access. Worked great!

However, when I boot the computer I get the current 3.x kernels that have been installed through PP updates AND I also get the 2.6.x kernels that are on the two IDE drives that were originally main HDDs in my old computer.

I would like to get rid of the old kernels. I cannot simply go into Synaptic and remove them that way since they weren't installed that way. I have a separate /boot partition on one of the drives. Can I just format that small partition to get rid of the kernels on that drive and then run "sudo update-grub" to remove them from the grub menu?

Robert

---

### Post by oldfred on 2012-01-31
I would not be running 12.04 as my main system until after April. It may break at any time as it is having a lot of changes and updates.

I might keep the possibly of booting old systems until then.

If you are not going to boot old system you can delete & reformat partition(s) to use as data partitions.

You can also just hide the other boot entires:
HOWTO: Grub Customizer Updated for grub 1.99
[http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html](http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html) 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
The Grub 2 Guide (formerly Grub 2 Basics) manual way
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Why I have an Ubuntu version on every drive:
Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

---

