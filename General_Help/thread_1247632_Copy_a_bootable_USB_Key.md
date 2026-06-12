---
title: "Copy a bootable USB Key ?"
date: 2009-08-23
forum: General Help
---

### Post by MikeV8 on 2009-08-23
Hello Folks,

I've spent considerable time installing and tweaking a distro for Mythbuntu to match  hardware and drivers needed, and wish to make this a distributable package on a USB key.  In essence, my platform is bootable from the USB key, and I now want to duplicate that bootable USB key to others so that I can duplicate the whole package (Mythbuntu on USB key, Netbook, TV kit/monitor etc).

Anyone know of an easy way to make an exact copy of a bootable (linux) USB key.  OR, at least to make a bootable ISO from the USB Key  (as there are lots of utilities that can take an ISO and create a bootable USB key from it) ?

---

### Post by P4man on 2009-08-23
dd!

```
dd if=/dev/yourbootableusbstick of=/dev/yournewusbstick
```

or you can make an image

```
dd if=/dev/yourusbstick of=usbimage.img

```

thats assuming the new stick is same size or larger as the old one. If its larger you'll have unpartitioned free space on it.

---

### Post by ujodarko on 2009-08-25
It seems very easy but can you help me a little bit more?

How to determine name of USB key so I could put it instead of "yourusbstick" in dd if=/dev/yourusbstick of=usbimage.img command?

I've made 9.04 boot USB on Transcend JF V30 4GB key using UNetbootin and it works well. Of course, I miss saving settings and installed programs>wondering how is it possible to install or make a file but after reboot those are not present?!

Is there some script that makes cleaning or ..?

---

### Post by P4man on 2009-08-25
> **ujodarko said:**
> It seems very easy but can you help me a little bit more?

How to determine name of USB key so I could put it instead of "yourusbstick" in dd if=/dev/yourusbstick of=usbimage.img command? 

In a terminal, type ```
sudo fdisk -l
```

as an example, on my machine I get:

```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed7ced7c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38913   312568641   83  Linux

Disk /dev/sdb: 1017 MB, 1017118720 bytes
64 heads, 32 sectors/track, 970 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0xa3994c70

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         722      739328   17  Hidden HPFS/NTFS

Disk /dev/sdb1: 757 MB, 757071872 bytes
64 heads, 32 sectors/track, 722 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0xa3994c70

     Device Boot      Start         End      Blocks   Id  System
/dev/sdb1p1   *           1         722      739328   17  Hidden HPFS/NTFS

Disk /dev/sdc: 4047 MB, 4047503360 bytes
255 heads, 63 sectors/track, 492 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ca380

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         492     3951958+  83  Linux

```

sda is my harddisk. sda1 is the first partition of that harddisk. sdb and and sdc are 2 USB keys of 1 and 4GB. If you have 2 keys with the same size, I suggest you plug 1 in, run fdisk -l, note the name, then plug the other one in, and run it again, and see which one was added.

In your dd command you want to use the device name, not the partition name. So for instance, "/dev/sdg" and **not** "/dev/sdg1' as that would be the partition, and then you wont be copying master boot record and stuff outside the partition.

> I've made 9.04 boot USB on Transcend JF V30 4GB key using UNetbootin and it works well. Of course, I miss saving settings and installed programs>wondering how is it possible to install or make a file but after reboot those are not present?!

Is there some script that makes cleaning or ..?

To be able to save settings on a live.. well, stick, you need to make a "persistent" live install (google is your friend, a gazillion howto's out there). And if im not mistaken, you must create a user other than the default ubuntu user (which gets deleted and recreated upon each boot IIRC).

---

### Post by ujodarko on 2009-08-25
> **P4man said:**
> 

To be able to save settings on a live.. well, stick, you need to make a "persistent" live install (google is your friend, a gazillion howto's out there). And if im not mistaken, you must create a user other than the default ubuntu user (which gets deleted and recreated upon each boot IIRC).

OK! I understood everything.

My key is sda ;-)

I am just wondering... it makes me happy ;-)... I wonder what should we do to force leaving files and programs on live session user account? In other words, what changes of what files should I change to make that account not deleted during reboot?

Am I asking too much :-D ?

p.s. it seems my Transcend key is *ill* cause it won't show up under USB Startup Disk Creator > that is why I used UNetbootin under XP

---

