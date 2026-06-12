---
title: "Unable to Mount Ubuntu Partition"
date: 2011-05-09
forum: General Help
---

### Post by mattrob33 on 2011-05-09
I was dual-booting Ubuntu (10.10) and Windows 7. I installed Backtrack in addition to these 2, and the Ubuntu GRUB was replaced with the one from Backtrack.

Now when I boot, only Backtrack and Windows 7 are listed in GRUB. When I run fdisk from Backtrack, I see all partitions, and running a Partition Manager lists the Ubuntu partition as a Linux partition. However, the partition manager says that it is unable to read the contents of the partition, and that it is unable to re-read the partition table.

Any ideas? Thanks in advance.


Also, the Ubuntu, Backtrack, and Linux Swap partition are all listed under the same Extended partition.

---

### Post by tredegar on 2011-05-09
Your ubuntu partition is probably formatted as ext4 and backtrack may not be able to cope with this (Aside: Why are you running backtrack?).

I think you need to restore grub2. Here are a couple of links to help you...
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html](http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html)

---

### Post by WorMzy on 2011-05-09
I believe Backtrack is based on Debian Lenny, which I think uses grub legacy. You have two options: 1) Update your grub legacy's menu.lst to allow you to boot Ubuntu, or 2) Reinstall grub 2 and update it so it knows about Backtrack.

Option 2 is probably best if you want to receive support on this forum (since Ubuntu uses Grub 2 by default), though I would personally stick with Grub legacy.

tredegar has posted links which will help you with 2), if you'd prefer to go with 1), please post the output of these commands:

```
sudo fdisk -l
```
```
sudo blkid
```

then mount your Ubuntu partition and post the output of this command:
```
ls /media/<ubuntu mount point>/boot
```

---

### Post by mattrob33 on 2011-05-10
.

---

### Post by mattrob33 on 2011-05-10
The Ubuntu partition I want to access is sda5.

Also, I messed up GRUB and had to use recovery mode. From there, I was able to manually boot Backtrack (sda7) but was not able to even ls my Ubuntu partition.


Output:

```
sudo fdisk -l
```Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8e0f36f2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        2300    18432000    7  HPFS/NTFS
/dev/sda3            2300       33213   248309557+   7  HPFS/NTFS
/dev/sda4           33213       60802   221603840+   5  Extended
/dev/sda5           33213       48878   125829120   83  Linux
/dev/sda6           59700       60802     8847360   82  Linux swap / Solaris
/dev/sda7           48879       59699    86919651   83  Linux




```
sudo blkid
```/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="3030-3030" TYPE="vfat"
/dev/sda5: UUID="adc5ef23-4dd7-4fd1-a15f-57a314e172a5" TYPE="ext4"
/dev/sdb5: UUID="532464e8-0659-436e-8b50-0fb0290abbb2" TYPE="swap"
/dev/sda2: UUID="DC2E713E2E71132E" LABEL="RECOVERY" TYPE="ntfs"
/dev/sda3: UUID="92E6732AE6730E2B" LABEL="OS" TYPE="ntfs"
/dev/sda6: TYPE="swap" UUID="9bada277-a781-4cf3-b5dc-657a051dad82"
/dev/sda7: UUID="2292ebf3-4501-40d1-bc73-c94f068ce8e7" TYPE="ext3"
/dev/sdb1: LABEL="BACKTRACK" UUID="A223-D903" TYPE="vfat"




```
ls /media/<ubuntu mount point>/boot
```System.map-2.6.35-28-generic  initrd.img-2.6.35-29-generic
System.map-2.6.35-29-generic  memtest86+.bin
abi-2.6.35-28-generic         memtest86+_multiboot.bin
abi-2.6.35-29-generic         vmcoreinfo-2.6.35-28-generic
config-2.6.35-28-generic      vmcoreinfo-2.6.35-29-generic
config-2.6.35-29-generic      vmlinuz-2.6.35-28-generic
grub                          vmlinuz-2.6.35-29-generic
initrd.img-2.6.35-28-generic

---

### Post by tredegar on 2011-05-10
sda5 (where you have ubuntu) is an **ext4** formatted partition. I don't think backtrack or "grub legacy" can be relied on to deal with **ext4** correctly. You will note that **sda7** (backtrack) is formatted as **ext3**

But the bottom line is that you need to boot from an ubuntu live CD and reinstall **grub2**.

Here is the exact link: [Reinstall GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

---

### Post by WorMzy on 2011-05-10
Alright, a grub legacy entry for your Ubuntu installation would look like this:

```
title        Ubuntu - kernel 2.6.35-29-generic
root         (hd0,4)
kernel       /boot/vmlinuz-2.6.35-29-generic root=UUID=adc5ef23-4dd7-4fd1-a15f-57a314e172a5 ro quiet splash
initrd       /boot/initrd.img-2.6.35-29-generic
```

However, what do you mean by "I messed up GRUB and had to use recovery mode."? What did you do to mess up Grub?


> **tredegar said:**
> I don't think backtrack or "grub legacy" can be relied on to deal with **ext4** correctly.

This is incorrect. Grub legacy can read ext4 perfectly fine. Most of my partitions are ext4, and I use Grub legacy.

---

### Post by mattrob33 on 2011-05-10
Ok I reinstalled grub2 from a Live CD and finally regained access to my Ubuntu partition -- I am on it now. Marking thread as solved -- thanks to everyone who helped.

---

