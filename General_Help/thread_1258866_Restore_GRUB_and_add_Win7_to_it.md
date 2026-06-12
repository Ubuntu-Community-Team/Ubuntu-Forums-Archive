---
title: "Restore GRUB and add Win7 to it"
date: 2009-09-05
forum: General Help
---

### Post by demontager on 2009-09-05
The state is , I have 3 partitions on Hard drive, one with Ubuntu, one with Windows7 installed. But first installed Ubuntu, so Win7 loader wiped GRUB as usually. 
So I need restore GRUB and and Win7 loader to Grub menu
What I did.
1. Booted from LiveUSB Ubuntu
2. Checked partitions state:
```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x649d1964

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       16145       29786   109579365    7  HPFS/NTFS
/dev/sda2           29787       30401     4939987+  82  Linux swap / Solaris
/dev/sda3               1       16144   129676648+  83  Linux


```
3. Then entered in terminal grub, and point to place where stage1 installed:
```

grub> find /media/disk-1/boot/grub/stage1
find /media/disk-1/boot/grub/stage1

Error 15: File not found
grub> 

```
But why it can't find it? For sure it is exactly there, I can make cd to that directory

---

### Post by louieb on 2009-09-05
at the **grub>** prompt try 
```
find /boot/grub/stage2
```

From looking at the fdisk output should return (hd0,2)

---

