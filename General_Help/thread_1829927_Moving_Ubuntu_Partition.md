---
title: "Moving Ubuntu Partition"
date: 2011-08-21
forum: General Help
---

### Post by wotte3 on 2011-08-21
I was triple booting windows 7, kubuntu and ubuntu (both 11.04) and i deleted the kubuntu partition. i now have unallocated space between my windows and ubuntu partition. is there a way to move my ubuntu partition over and still be able to boot into GRUB? i am afraid that if i move it, when i start up the computer will not be able to find the GRUB bootloader because the partition has been moved.

---

### Post by fdrake on 2011-08-21
> **wotte3 said:**
> I was triple booting windows 7, kubuntu and ubuntu (both 11.04) and i deleted the kubuntu partition. i now have unallocated space between my windows and ubuntu partition. is there a way to move my ubuntu partition over and still be able to boot into GRUB? i am afraid that if i move it, when i start up the computer will not be able to find the GRUB bootloader because the partition has been moved.

can you post a screenshot of your GParted scheme of the disk.

if you don't have gparted do
```

sudo apt-get install gparted
```

or just post the putput of
```

sudo fdisk -l

```

---

### Post by wotte3 on 2011-08-21
here you go:

```

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x80cda15e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          13      102400   de  Dell Utility
Partition 1 does not end on cylinder boundary.
/dev/sda2   *          13        1926    15360000    7  HPFS/NTFS
/dev/sda3            1926       84318   661813112    7  HPFS/NTFS
/dev/sda4           84318       91202    55297025    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5           86263       90183    31489024   83  Linux
/dev/sda6           90183       91202     8180736   82  Linux swap / Solaris
```

---

### Post by fdrake on 2011-08-21
ok if you want the extended unloccated partition to be part of the linux partition do this:

1. reboot from a live cd
2. use gparted (make sure you have all partition unmounted) and increase the linux (sda5) partition by moving the arrow-side forward.
3.apply the changes and reboot again from the live cd
4.open the terminal and type:
    ```

sudo mount -a
grub
>find /boot/grub/stage1
(it shoud give you as output sda,5 or sd.4)
>root (sda,5) # or (sda,4)whatever the previous command outputted
>setup (sda,5) # or (sda,4)whatever the find command outputted
>quit

```

or you can simply format the unllocated size to an ext3 partition or a NTFS/FAT32 partition so you can share it with both ubunu and windows and mount it in a folder of your choice.

the second suggestion is less risky since your system uses a windows mbr too, in sda2.

---

### Post by YesWeCan on 2011-08-21
Yes, GParted can be used to resize sda5 and drag its start to the left to fill the unallocated space. Grub may break tho and on reboot you'll probably see a grub rescue prompt. If you have a problem youll need to reinstall it.
It depends which type of grub you have. fdrake's method is for grub legacy. For Grub2 you can boot your 11.04 live CD/USB and do
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

---

