---
title: "Hp Recovery option"
date: 2010-09-06
forum: General Help
---

### Post by psycho5 on 2010-09-06
I have a delimma,

I resized my disk in my hp mini to create 27gb from the windows partition using the ubuntu live usb to install ubuntu netbook remix. 

After installation, the grub menu had 2 windows loaders.

Windows Vista (Loader) which actually boots the recovery partition that came with the pc.

The other one Windows 7 (loader) is my Windows. But it doesn't boot up, the windows loader shows up saying that a recent hardware or software change might be the cause, the boot failed because a required device is inaccessible, please run the "repair my computer" from the windows boot cd.

I created a windows 7 usb boot disk, and did that, but no avail. I also went to command prompt and from X:>bootsect /nt60 C:\ also same problem. 

```

oj@oj-laptop:~$ sudo fdisk -l
[sudo] password for oj:
 
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb8ba0d59
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3432    27567446+   5  Extended
/dev/sda2            3433       28896   204539580    7  HPFS/NTFS
/dev/sda3           28897       30389    11978752    7  HPFS/NTFS
/dev/sda4           30389       30402      105656    c  W95 FAT32 (LBA)
/dev/sda5             128        3432    26547412+  83  Linux
/dev/sda6               1         127     1020033   82  Linux swap / Solaris
 
Partition table entries are not in disk order
oj@oj-laptop:~$

```

Partition table entries are not in disk order, is this a big concern? Could it be a reason why windows isn't booting?

I want to know if I use HP's recovery option to restore windows, will it wipe out my Ubuntu? Or will it just work on the C:\ drive? It has two options, Restore Factory settings, or restore windows.

Need someone's opinion who has faced a similar situation.

---

### Post by psycho5 on 2010-09-06
any help would be appreciated =)

---

