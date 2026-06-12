---
title: "Unable to mount 52 GB LVM2 Physical Volume"
date: 2011-07-10
forum: General Help
---

### Post by Tijmens on 2011-07-10
When I installed Ubuntu, I created an 52 gb encrypted partition which shows up in the disk utility, and in the window that opens when I click on the "home folder" icon. I get my normal windows partition, and under that the 52 GB LVM2 partition. But when I try to access it, I get this error.

Unable to mount 52 GB LVM2 Physical Volume - not a mountable file system

This is what fdisk -l shows

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          52      409600   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2              52       30452   244193280    7  HPFS/NTFS
/dev/sda3           30452       54427   192580608   8e  Linux LVM
/dev/sda4           54428       60802    51200001    5  Extended
/dev/sda5           54428       54488      487424   83  Linux
/dev/sda6           54488       60802    50711552   83  Linux

This is what lvmdiskscan shows. Not sure why it says 25 partitions.

  /dev/ram0  [      64.00 MiB] 
  /dev/loop0 [     100.00 GiB] 
  /dev/dm-0  [      48.36 GiB] LVM physical volume
  /dev/ram1  [      64.00 MiB] 
  /dev/sda1  [     400.00 MiB] 
  /dev/root  [       4.66 GiB] 
  /dev/ram2  [      64.00 MiB] 
  /dev/sda2  [     232.88 GiB] 
  /dev/dm-2  [       1.86 GiB] 
  /dev/ram3  [      64.00 MiB] 
  /dev/sda3  [     183.66 GiB] LVM physical volume
  /dev/dm-3  [       9.31 GiB] 
  /dev/ram4  [      64.00 MiB] 
  /dev/dm-4  [       1.86 GiB] 
  /dev/ram5  [      64.00 MiB] 
  /dev/sda5  [     476.00 MiB] 
  /dev/dm-5  [     100.00 GiB] 
  /dev/ram6  [      64.00 MiB] 
  /dev/sda6  [      48.36 GiB] 
  /dev/ram7  [      64.00 MiB] 
  /dev/ram8  [      64.00 MiB] 
  /dev/ram9  [      64.00 MiB] 
  /dev/ram10 [      64.00 MiB] 
  /dev/ram11 [      64.00 MiB] 
  /dev/ram12 [      64.00 MiB] 
  /dev/ram13 [      64.00 MiB] 
  /dev/ram14 [      64.00 MiB] 
  /dev/ram15 [      64.00 MiB] 
  1 disk
  25 partitions
  0 LVM physical volume whole disks
  2 LVM physical volumes

How can I fix this, and be able to access that 52gb partition? This is only my second day that I work with Ubuntu, so If more information is needed then let me know :)

---

### Post by Habitual on 2011-07-10
have you rebooted?

---

### Post by Tijmens on 2011-07-10
Yeah multiple times, I had this problem since yesterday but haven't the time to look into it until today.

---

### Post by bodhi.zazen on 2011-07-10
Hard to tell from what little you have posted.

See the documentation on how to manage LUKS and a LVM for details.

Here is a simple how to mount the partition:

[http://www.ubuntugeek.com/rescue-an-encrypted-luks-lvm-volume.html](http://www.ubuntugeek.com/rescue-an-encrypted-luks-lvm-volume.html)

As your LVM is listed, I assume the problem is with configuration of your LVM and / or fstab ?

This how to reviews how to configure your partitions:

[http://www.debuntu.org/how-to-encrypted-partitions-over-lvm-with-luks](http://www.debuntu.org/how-to-encrypted-partitions-over-lvm-with-luks)

In particular see the last part about configuration of your LVM and mount points.

If you need assistance you will need to provide additional information, the contents of 

/etc/crypttab
/etc/fstab

;)

---

### Post by Tijmens on 2011-07-12
I installed a tool called called "Logic Volume Management" that showed that I forgot to format a big part of that 52 Gb Partition. That was the part that I was hoping to show up onder the "Home Folder" link in Ubuntu. The whole Ubuntu partition is 52 GB, and that part is now 33 GB. I managed to mount it under /files , but it didn't really change my problem.

The "Home Folder" still shows both the windows partitions and the 52 GB LVM2 Physical Volume,  and the last one comes up with the error when you try to access it.

Here is the content of the crypttab and the fstab

/etc/crypttab
---------------
sda6_crypt UUID=79d79d55-9d9c-4162-acd7-4031ae2850c0 none luks
cryptswap1 /dev/dm-2 /dev/urandom swap,cipher=aes-cbc-essiv:sha256

/etc/fstab
---------------
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/HU-root /               ext4    errors=remount-ro 0       1
/dev/sda5       /boot           ext2    defaults        0       2
/dev/mapper/HU-home /home           ext4    defaults        0       2
/dev/mapper/HU-swap none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
/dev/HU/files           /files          ext4    defaults        1 2

I noticed that the  root / home / swap / cryptswap are mounted under /dev/mapper/ and the files under /dev/hu. Could that be an issue?

---

### Post by bodhi.zazen on 2011-07-12
List the devices in /dev/mapper

```
ls /dev/mapper
```

And look at your logical volumes 

```
lvdisplay
```

---

### Post by Tijmens on 2011-07-13
ls /dev/mapper shows this

```

control  cryptswap1  HU-files  HU-home    HU-root  HU-swap  sda6_crypt

```

lvdisplay come up with this list.

```

 --- Logical volume ---
  LV Name                /dev/HU/root
  VG Name                HU
  LV UUID                Z2j9g3-JPz3-NTNH-hr2U-7ME4-NJX5-GCr7a3
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                4.66 GiB
  Current LE             1192
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     3072
  Block device           252:1
   
  --- Logical volume ---
  LV Name                /dev/HU/swap
  VG Name                HU
  LV UUID                ufaBDB-fU3d-vxQ1-QOnu-QnGM-I2QC-1FLoX4
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                1.86 GiB
  Current LE             476
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:2
   
  --- Logical volume ---
  LV Name                /dev/HU/home
  VG Name                HU
  LV UUID                7MTMNr-NM90-GPgL-vgNu-Wpuv-Q2hk-b2d7Tu
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                9.31 GiB
  Current LE             2384
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     3072
  Block device           252:3
   
  --- Logical volume ---
  LV Name                /dev/HU/files
  VG Name                HU
  LV UUID                GGcdwd-S76r-RM2F-GkV1-sXpT-t0aJ-2xtQMs
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                32.53 GiB
  Current LE             8328
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     3072
  Block device           252:4

```

---

### Post by bodhi.zazen on 2011-07-13
Looks fine to me. Devices are often cross referenced, by label, bu uuid, etc.
[FONT=monospace]
[/FONT]/dev/HU/files looks == /dev/mapper/HU-files

Is everything working ?

---

### Post by psusi on 2011-07-13
You don't mount the LVM2 partition because it does not contain a filesystem.  The LVM2 partition is a physical volume that is used to provide backing storage for logical volumes.  In other words, it contains all of those filesystems you have in /dev/HU/.

You might want to read [https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm).

---

### Post by Tijmens on 2011-07-16
After reading the article it makes sense to me now why I can't access it. But is there a way to make the '52 GB LVM2 Physical Volume' not show up in the file explorer? Its a bit pointless for it to show up, I mean you can't click on it without getting an error. Is there anyway I could for example replace the link for the "52 GB LVM2 Physical Volume" into a link to the /files?

---

### Post by psusi on 2011-07-16
You mean it shows up in "Computer" and on the places menu?  It shouldn't.  Can you post your /etc/fstab file?

---

### Post by Tijmens on 2011-07-17
Yeah, the places menu is what I'm talking about.

This is the content of the /ect/fstab file

/dev/mapper/HU-root /               ext4    errors=remount-ro 0       1
/dev/sda5       /boot           ext2    defaults        0       2
/dev/mapper/HU-home /home           ext4    defaults        0       2
/dev/mapper/HU-swap none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
/dev/HU/files           /files          ext4    defaults        1 2

---

### Post by psusi on 2011-07-17
What about blkid?

---

