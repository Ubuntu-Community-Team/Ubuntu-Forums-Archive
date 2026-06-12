---
title: "Need to change incorrect UUID in Grub2 in 10.04"
date: 2010-11-28
forum: General Help
---

### Post by Garibaldi3489 on 2010-11-28
Hi Everyone,

I am working on setting up a server with Ubuntu 10.04. I have two drives set up as a raid as follows:
/dev/sda1     unused
/dev/sda2     / 
/dev/sdb1     /boot
/dev/sdb2     /

sda2 and sdb2 together form the raid, /dev/md0. This all worked fine during the install but grub2 does not seem to be recognizing the raid's UUID correctly. It is only seeing the UUID of /dev/sda2 and trying to boot that, which drops me back to a busybox at boot. I know the UUID of the raid and would like to simply change the grub entry to it and then booting should hopefully work. 

I have tried update-grub and grub-install repeatedly with no luck because it cannot seem to detect the raid's UUID over sda2's UUID. How can I update the UUID? I do not want to create a new custom menu entry in /etc/grub.d/40_custom. Is there a way to use the existing menu entry?

Thanks!

Also, this problem may be related to [the one described here](http://ubuntuforums.org/showthread.php?t=1474950).

---

### Post by dcstar on 2010-11-30
> **Garibaldi3489 said:**
> 
.......
I have tried update-grub and grub-install repeatedly with no luck because it cannot seem to detect the raid's UUID over sda2's UUID. How can I update the UUID? I do not want to create a new custom menu entry in /etc/grub.d/40_custom. Is there a way to use the existing menu entry?
.......

[http://www.linuxquestions.org/questions/linux-general-1/raid-and-grub-2-on-ubuntu-karmic-koala-788540/](http://www.linuxquestions.org/questions/linux-general-1/raid-and-grub-2-on-ubuntu-karmic-koala-788540/)
[http://www.howtoforge.com/how-to-set-up-software-raid1-on-a-running-system-incl-grub2-configuration-ubuntu-10.04-p3](http://www.howtoforge.com/how-to-set-up-software-raid1-on-a-running-system-incl-grub2-configuration-ubuntu-10.04-p3)

---

### Post by Garibaldi3489 on 2010-12-07
Thanks for the quick and informative reply. The solution ended up being that I needed to manually specify the partitions in the raid in /etc/mdadm/mdadm.conf. Before, it looked like:
```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions
```

After, it only specified /dev/sda2 and dev/sdb2, the partitions in the raid:
```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE /dev/sda2, dev/sdb2
```

This change allowed it to boot properly. Thanks again!

---

### Post by dcstar on 2010-12-08
> **Garibaldi3489 said:**
> 
.........
This change allowed it to boot properly. Thanks again!

Then READ BELOW!

---

### Post by indulis on 2011-05-11
The wrong UUID is stored in the copy of mdadm.conf in your initrd (initrdXXXXXXX) file (in /boot).  This is used to buid a "mini-filesystem" that is used during the boot process.  Until you update it you will have troubles.  Use update-initramfs from your working system.  

If desperate you can cpio/unzip the initrd file in another filesystem (say a USB key mounted when running a rescue CD or live CD), manually modify the file, then write it back.  I wrote up how to get through a non-working GRUB2 boot here [http://serverfault.com/questions/180138/software-raid-mdadm-not-adding-spare/268659#268659]("http://serverfault.com/questions/180138/software-raid-mdadm-not-adding-spare/268659#268659").  Basically you boot up in grub, modify the boot line to remove the "quiet" and "splash", let it boot and fail, which drops you into initramfs.  Then manually modify/create your mdadm.conf, "mdadm --assemble" the RAID device, and "exit" from initramfs to resume the grub boot with a working md RAID array.  Hopefully GRUB2 finds it (if using partition labels or LVM you should be OK).

---

