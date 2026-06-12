---
title: "Fatal Error: Bad primary partition 1: Partition ends after end-of-disk"
date: 2010-06-12
forum: General Help
---

### Post by chinmaya_n on 2010-06-12
Hi...

I've tried to install Arch but when I select HardDisk > Manual during installation.. It asks me getting into cfdisk and cfdisk shows this error Fatal Error: Bad primary partition 1: Partition ends after end-of-disk.

I've Ubuntu on my system and I executed cfdisk and it showed no errors and fdisk -l too sad
Both of them showed no errors but while installing only it is showing like that ! smile Its weird !
I tried to google , but I didnt get what to do with that.

Plz help me... smile New Arch Bee

```
cfdisk (util-linux-ng 2.16)

                              Disk Drive: /dev/sda
                       Size: 320072933376 bytes, 320.0 GB
             Heads: 255   Sectors per Track: 63   Cylinders: 38913

    Name        Flags      Part Type  FS Type          [Label]        Size (MB)
 ------------------------------------------------------------------------------
    sda1        Boot        Primary   Linux ext3                       40073.57
    sda5                    Logical   Linux ext3                      199997.69
    sda6                    Logical   Linux swap / Solaris              3002.23
    sda7                    Logical   W95 FAT32                        56992.97
    sda8                    Logical   Linux ext3                       20003.89
```
```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0aaf0aaf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4872    39134308+  83  Linux
/dev/sda2            4873       38913   273434332+   5  Extended
/dev/sda5            4873       29187   195310206   83  Linux
/dev/sda6           29188       29552     2931831   82  Linux swap / Solaris
/dev/sda7           29553       36481    55657161    b  W95 FAT32
/dev/sda8           36482       38913    19535008+  83  Linux
```

---

### Post by dino99 on 2010-06-12
check your partitions with tool like partedmagic

[http://partedmagic.com/](http://partedmagic.com/)

---

### Post by srs5694 on 2010-06-12
Post the results of "fdisk -lu". This changes the reporting units of fdisk from cylinders to sectors, which may turn up the cause of the problem. Also, check [my Web page on this sort of problem.](http://www.rodsbooks.com/missing-parts/index.html)

---

### Post by chinmaya_n on 2010-06-12
> **srs5694 said:**
> Post the results of "fdisk -lu".
```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0aaf0aaf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    78268679    39134308+  83  Linux
/dev/sda2        78268680   625137344   273434332+   5  Extended
/dev/sda5        78268743   468889154   195310206   83  Linux
/dev/sda6       468889218   474752879     2931831   82  Linux swap / Solaris
/dev/sda7       474752943   586067264    55657161    b  W95 FAT32
/dev/sda8       586067328   625137344    19535008+  83  Linux

```

---

### Post by srs5694 on 2010-06-12
I don't see anything wrong with those partitions, but it's possible I've missed something. Verify for yourself that the partitions don't overlap (with the exception of /dev/sda2, which must contain /dev/sda5 through [noparse]/dev/sda8[/noparse] and that they all end before the last sector on the disk.

Do you have any other disks in the computer? Even removable disks like USB flash drives? If so, try removing them when you install Arch.

---

### Post by chinmaya_n on 2010-06-13
> **srs5694 said:**
> 
Do you have any other disks in the computer? Even removable disks like USB flash drives? If so, try removing them when you install Arch.
I don't 've any other drives and also USB flash drives..! :(
I'm trying a lot! But not getting anything!:confused:

---

### Post by chinmaya_n on 2010-06-13
> **dino99 said:**
> check your partitions with tool like partedmagic

[http://partedmagic.com/](http://partedmagic.com/)

It did nt yield any results :(
Guys.. what should I do! ?

---

### Post by chinmaya_n on 2010-06-14
bump :(

---

### Post by chinmaya_n on 2010-06-16
I have deleted sda8 and reduced the sda2 partition and freed  that space...! (by using a live CD)

Haha.. I could install Arch now!! but I got stuck when it asked to install grub in which partition!! I didn't know on which partition MBR was!!
So i installed it on an external flash drive.... ( I thought i could change later or copy later to MBR)
But My system is not booting by using that Flash drive !! My system has ubuntu 9.10 also!
So, Can I write in the grub list of ubuntu so.. that it can boot into that partition !!

These are the things I could find in the menu.lst of arch
```
# (0) Arch Linux
title  Arch Linux
root   (hd0,7)
kernel /boot/vmlinuz26 root=/dev/sda8 ro
initrd /boot/kernel26.img

# (1) Arch Linux
title  Arch Linux Fallback
root   (hd0,7)
kernel /boot/vmlinuz26 root=/dev/sda8 ro
initrd /boot/kernel26-fallback.img
```
How to write this into my list.... **grub.cfg**

---

### Post by chinmaya_n on 2010-06-16
I just made it..... just by using:
```

grub-mkconfig -o /boot/grub/grub.cfg
```
Thanx guys...!

---

