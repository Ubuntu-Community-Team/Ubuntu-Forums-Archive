---
title: "Unable to boot"
date: 2012-02-07
forum: General Help
---

### Post by sshaikh on 2012-02-07
Hi all,

I run Ubuntu in a Hyper-V VM. Due to power failure, the box hard reset. Most of my VMs survived, but one didn't. On boot I get the normal GRUB menu and then a error: Out Of Partition, and get some kind of kernel panic due to not being able to mount a VFS.

I am able to get a shell via rescue mode on the CD which seems to detect my root filesystem. I use LVM and have one root and a swap. On fdisk -l I see the following:

[IMG]http://i.imgur.com/cMV2c.png[/IMG]

Any ideas on how to fix this? I tried some of the tips on [http://ubuntuforums.org/showthread.php?t=1743697](http://ubuntuforums.org/showthread.php?t=1743697) but that seems to have only replaced an already working GRUB menu with a GRUB command line.

Thanks in advance!

---

