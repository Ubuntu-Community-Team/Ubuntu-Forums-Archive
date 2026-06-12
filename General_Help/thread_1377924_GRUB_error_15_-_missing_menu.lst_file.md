---
title: "GRUB error 15 - missing menu.lst file"
date: 2010-01-10
forum: General Help
---

### Post by alejandro910 on 2010-01-10
Hi.. I have a pc that double boots Ubuntu Linux and Windows 7..

I 've downloaded the latest version of Ubuntu, 9.1, burned the iso and then had a clean install of Ubuntu, over the last version.. 

After the reboot, GRUB stopped working printing ERROR 15.

SuperGrub disk did nothing, so I opened Ubuntu Live and checked my hard disk for /boot/grub/menu.lst but I couldn't find it..

Is there any way tou create a new menu.lst or solve my problem?

thnx

---

### Post by Crafty Kisses on 2010-01-10
Let's see the partition table, maybe from there I can help you, post the results of the following:
```
sudo fdisk -l
sudo fdisk -lu
```

---

### Post by Leppie on 2010-01-10
> **alejandro910 said:**
> I 've downloaded the latest version of Ubuntu, 9.1, burned the iso and then had a clean install of Ubuntu, over the last version.. 

After the reboot, GRUB stopped working printing ERROR 15.

SuperGrub disk did nothing, so I opened Ubuntu Live and checked my hard disk for /boot/grub/menu.lst but I couldn't find it..

Is there any way tou create a new menu.lst or solve my problem?

thnx

karmic ships with grub2 which doesn't use menu.lst but grub.cfg.
booting with the livecd, try this:
```
sudo mount /dev/sda5 /mnt  ##replace /dev/sda5 with your linux partition
sudo grub-install --recheck --root-directory=/mnt /dev/sda
```

---

### Post by alejandro910 on 2010-01-10
@Crafty Kisses

here is the result for fdisk -l

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00068d1a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3825    30724281    7  HPFS/NTFS
/dev/sda2            3826       11475    61448625    7  HPFS/NTFS
/dev/sda4           11476       30401   152023095    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5f4d45c9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5193    41712741    7  HPFS/NTFS
/dev/sdb2            5194        9259    32660145   83  Linux
/dev/sdb3            9260        9729     3775275   82  Linux swap / Solaris

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdfb0c826

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19456   156280288+   7  HPFS/NTFS

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8d399bc0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60800   488375968+   7  HPFS/NTFS

```and for fdisk -lu

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00068d1a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    61448624    30724281    7  HPFS/NTFS
/dev/sda2        61448625   184345874    61448625    7  HPFS/NTFS
/dev/sda4       184345875   488392064   152023095    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5f4d45c9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    83425544    41712741    7  HPFS/NTFS
/dev/sdb2        83425545   148745834    32660145   83  Linux
/dev/sdb3       148745835   156296384     3775275   82  Linux swap / Solaris

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdfb0c826

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   312560639   156280288+   7  HPFS/NTFS

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8d399bc0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63   976751999   488375968+   7  HPFS/NTFS

```
@Leppie

> ubuntu@ubuntu:~$ sudo grub-install --recheck --root-directory=/mnt /dev/sda
Installation finished. No error reported.
This is the contents of the device map /mnt/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)    /dev/fd0
(hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sdc
(hd3)    /dev/sdd

I replaced sda5 with sdb2 and didn't work.. sdb2 is my linux partition, right?

---

### Post by Leppie on 2010-01-10
> **alejandro910 said:**
> ```
Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5f4d45c9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5193    41712741    7  HPFS/NTFS
**/dev/sdb2            5194        9259    32660145   83  Linux**
/dev/sdb3            9260        9729     3775275   82  Linux swap / Solaris
```


@Leppie

I replaced sda5 with sdb2 and didn't work.. sdb2 is my linux partition, right?
yes, sdb2 is your linux partition.
which drive is set to boot first in your bios? are they all sata drives?

---

### Post by alejandro910 on 2010-01-10
no, only one is SATA.. 2 of them are USB ext.. i have ubuntu on IDE hard disk..

I think the SATA disk is set to boot first, but I had no problems in the past!

---

### Post by mr clark25 on 2010-01-10
you might try chrooting into your system and then running "update-grub" do this by:

> **Leppie said:**
> 
```
$sudo bash
$mkdir -p /mnt/temp/boot
$mount /dev/sda6 /mnt/temp/
$mount -o bind /proc /mnt/temp/proc
$mount -o bind /dev /mnt/temp/dev
$mount -o bind /dev/pts /mnt/temp/dev/pts
$mount -o bind /sys /mnt/temp/sys
$chroot /mnt/temp
$update-grub
$exit
```


i am having my second problem with grub, and know that its not fun.

---

### Post by Leppie on 2010-01-10
ok, with the same configuration, update your grub.cfg:
```
sudo update-grub
```

---

### Post by alejandro910 on 2010-01-10
> **mr clark25 said:**
> you might try chrooting into your system and then running "update-grub" do this by:




i am having my second problem with grub, and know that its not fun.


root@ubuntu:~# mount -o /sys /mnt/temp/sys
mount: can't find /mnt/temp/sys in /etc/fstab or /etc/mtab

---

### Post by Leppie on 2010-01-10
> **alejandro910 said:**
> root@ubuntu:~# mount -o /sys /mnt/temp/sys
mount: can't find /mnt/temp/sys in /etc/fstab or /etc/mtab
this procedure is only for when booting off the livecd, i believe you are still working in your installed system, am i right?

---

### Post by alejandro910 on 2010-01-10
> **Leppie said:**
> ok, with the same configuration, update your grub.cfg:
```
sudo update-grub
```

ubuntu@ubuntu:~$ sudo update-grub
grub-probe: error: cannot find a device for /.

---

### Post by alejandro910 on 2010-01-10
> **Leppie said:**
> this procedure is only for when booting off the livecd, i believe you are still working in your installed system, am i right?

i'm working with the livecd.. i cannot normally boot

---

### Post by Leppie on 2010-01-10
then amend the procedure like this:
```
sudo bash
mkdir -p /mnt/temp/boot
mount /dev/sdb2 /mnt/temp/
mount -o bind /proc /mnt/temp/proc
mount -o bind /dev /mnt/temp/dev
mount -o bind /dev/pts /mnt/temp/dev/pts
mount -o bind /sys /mnt/temp/sys
chroot /mnt/temp
grub-install --recheck /dev/sda
update-grub
exit
```

---

### Post by alejandro910 on 2010-01-10
> **Leppie said:**
> then amend the procedure like this:
```
sudo bash
mkdir -p /mnt/temp/boot
mount /dev/sdb2 /mnt/temp/
mount -o bind /proc /mnt/temp/proc
mount -o bind /dev /mnt/temp/dev
mount -o bind /dev/pts /mnt/temp/dev/pts
mount -o bind /sys /mnt/temp/sys
chroot /mnt/temp
grub-install --recheck /dev/sda
update-grub
exit
```

this gave me no errors, and i still can't boot in linux.. :(

but now i don't get the message for GRUB error, it boots in windows 7 :P

---

### Post by alejandro910 on 2010-01-11
well, I reinstalled ubuntu, but after the reboot, windows 7 is the OS that boots..

I changed hard disk boot priority from the bios menu and now GRUB works. But no menu appears and I can't boot on Windows. I have to change boot priority to that again.. 

Now i'm on ubuntu and i looked for grub.cfg file and there's no entry for windows.. How can I change this? I can't modify the file, it's read-only..

---

### Post by Leppie on 2010-01-11
which drive is the one booting now, the ide (sdb)?

---

### Post by alejandro910 on 2010-01-11
> **Leppie said:**
> which drive is the one booting now, the ide (sdb)?

yes.. the one with the linux partition

---

### Post by Leppie on 2010-01-11
then follow this:
```
sudo bash
mkdir -p /mnt/temp/boot
mount /dev/sdb2 /mnt/temp/
mount -o bind /proc /mnt/temp/proc
mount -o bind /dev /mnt/temp/dev
mount -o bind /dev/pts /mnt/temp/dev/pts
mount -o bind /sys /mnt/temp/sys
chroot /mnt/temp
grub-install --recheck /dev/sdb
update-grub
exit
```

---

### Post by alejandro910 on 2010-01-11
> root@alejandro:~# mount /dev/sdb2 /mnt/temp/
mount: you must specify the filesystem type

?

---

### Post by alejandro910 on 2010-01-13
i finally found a solution..

first I used fdisk to find my windows partition,  and then I followed a guide about GRUB2 and manually added a menu entry for windows..

thnx for your help :)

---

