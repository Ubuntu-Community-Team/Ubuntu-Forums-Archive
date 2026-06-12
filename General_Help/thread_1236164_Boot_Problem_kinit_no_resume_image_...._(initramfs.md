---
title: "Boot Problem: kinit :no resume image .... (initramfs)"
date: 2009-08-10
forum: General Help
---

### Post by zajith on 2009-08-10
Hi all,
I'm using Ubuntu 9.04 Desktop edition, 
Im getting the following while booting , pls help

Boot from (hd0,0) ext3 8801538........
Staring up....
Loading,Please wait....
19+0 records in
19+0 records out
kinit: name_to_dev_t(/dev/disk/by-uuid/9666......._) = dev(8,4)
kinit:trying to resume from /dev/disk/by-uuid/966.....
kinit:no resume image, doing normal boot....
mount:mounting /dev/disk/by-uuid/1b22b...... on /root
failed: Invalid argument
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed : No such file or directory
mount: mounting /proc on /root/proc failed : No such file or directory
Target filesystem doesnt have /sbin/init. 
No init found ,Try passing init=bootarg

BusyBox V1.10.2(Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter help for a list of built-in commands

(initramfs)
(initramfs)

thanks in advance...

---

### Post by petjakob on 2009-10-24
I have started getting these exact messages when I select my jaunty from grub. The odd thing is that it started when I changed grub to live on my PATA hard drive where linux is installed. Prior, I had had it on the SATA drive where windows was installed. 

I wish I could figure out why - if I just unhook the sata drive, error disappears. So I am thinking a workaround could be to now reload grub on the sata and go back to having it be hd0 in the bios. Windows is also able to boot fine from grub. I just don't want to mess up the mbr/windows 7 bootload so I want to keep grub on other drive.

The suggestion made on another thread I just turned up ([http://ubuntuforums.org/archive/index.php/t-1117956.html](http://ubuntuforums.org/archive/index.php/t-1117956.html)) by ronparent:

> Based on the boot errors you have posted, the first thing you need to know is whether or not the init file actually doesn't exist (if it does your ubuntu file system is probably intact)
.
Try from a live cd the commands:

grub
grub> find /sbin/init

If found, the output from that command will tell you that /sbin/init exist (and also that the file sysem probably is intact and where it resides). If so use that output as follows:

grub> root (hd?,?)
grub> setup (hdO)

This will set up your grub sot that you should again be able to boot into Linux (and Windows). If /sbin/init is not found, you may have to reinstall!!!?

---

### Post by petjakob on 2009-10-26
I fixed this issue by merely editing device.map, apparently my linux detects the drives as SDA1 = sata, sdb1 = pata, (so device.map swapped to read hd0 = sdb1, hd1=sda1) whereas in the bios i had forced the pata to be the first boot HD in order to let grub run from there.

I then had to edit the menu.lst to look for linux on hd0,0 but keep defining device location as /dev/sdb1.

---

### Post by yumpop on 2009-11-04
> **petjakob said:**
> I fixed this issue by merely editing device.map, apparently my linux detects the drives as SDA1 = sata, sdb1 = pata, (so device.map swapped to read hd0 = sdb1, hd1=sda1) whereas in the bios i had forced the pata to be the first boot HD in order to let grub run from there.

I then had to edit the menu.lst to look for linux on hd0,0 but keep defining device location as /dev/sdb1.

How you did that ???
I have the same problem... :\

---

