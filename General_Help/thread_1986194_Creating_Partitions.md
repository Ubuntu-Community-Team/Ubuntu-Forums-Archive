---
title: "Creating Partitions"
date: 2012-05-24
forum: General Help
---

### Post by Rockiholic on 2012-05-24
I'm looking for a little help creating additional partitions on my dual boot (12.04 and Win7)...

I would like to add another Linux distro on an additional partition w/o losing data.  I would also like to keep Ubuntu as my primary OS.  I have 55 GB of Free space, but I cant figure out how to move that free space into a new partition

Here is a pic of my current disk setup:
[IMG]http://i48.tinypic.com/11vtf6w.png[/IMG]


FYI: the 371 GB partition is Windows, and the 127 GB is Ubuntu 12.04

Thanks in advance

---

### Post by grahammechanical on 2012-05-24
I would suggest that the first thing that you do is install Grub Customizer in your 12.04 Ubuntu.

[http://ubuntuforums.org/showthread.php?t=1664134]("http://ubuntuforums.org/showthread.php?t=1664134")

This utility will give you some control over the Grub boot menu. It has a file menu Install to MBR option that is very useful. When we install another Linux distro or even another version of Ubuntu, the new install will put its own boot loader in the MBR. By running Grub Customizer you can put the 12.04 Grub boot menu back in the MBR.

Grub Customizer does other useful things as well.

Next, you need to be clear about what you want to do. We are only allowed 4 primary partitions but we can use one of those primary partitions as an Extended partition and then create any number of logical partitions inside the extended partition. As this is the partitioning setup that you now have.

Primary partitions = 1.6GB NTFS, 105MB NTFS, 371GB NTFS and 127GB Extended.

Logical partitions = 68GB Ext4 (Ubuntu? Yes?), 1.9 GB swap, 1.9 unknown and 55GB Free.

The simplest thing is to install this other Linux distro into the 55GB free space. with Disk Utility you can click on each partition and find out its number. Such as sda1, sda2, sda3 etc. You want to know what the number of the55GB free space is. Just to be clear that you are telling the installer where to install the new OS.

By the way you can shrink that 372Gb partition and expand that extended partition to create more space. You can also delete that 1.6GB partition if it is not needed and then expand the 55GB to take up to free (unallocated) space.

Oh, by the way. This new Linux distro should use the same swap space. It does not need it own swap space.

Regards.

---

### Post by km3952 on 2012-05-24
(In addition to what grahammechanical says)

In Linux terminology, your 55gb partition would be sda8. 1.9gb unknown would be sda7. Unless there is a reason for sda7 to exist, it could be deleted, before making a new partition for another Linux distro.

In a Linux terminal, run fdisk -l /dev/sda (as root or sudo), to see the partitioning scheme.

---

