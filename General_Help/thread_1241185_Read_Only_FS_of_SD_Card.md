---
title: "Read Only FS of SD Card"
date: 2009-08-15
forum: General Help
---

### Post by Cygoku on 2009-08-15
I have an SD card in wich I cannot copy or delete files because it says that it is a read only filesystem, how can I change that ?? 

Cygoku

---

### Post by tgalati4 on 2009-08-15
Open a terminal, post the output of:

dmesg | tail -30

Your card's filesystem probably has some sort of error that forces the kernel to mount is as ro (read-only).

Once you determine that it is indeed a filesystem error, then you can attempt to fix it.  First copy any critical files off the disk, since the repair may fail and require a reformat of the card.

What device is your card mounted as?

sudo fdisk -l

Let's say  it shows up as /dev/sde1

sudo fsck /dev/sde1

Follow the prompts.

---

### Post by Cygoku on 2009-08-16
> **tgalati4 said:**
> Open a terminal, post the output of:

dmesg | tail -30

.

There it is :

cygoku@shizzled:~$ dmesg | tail -30
[ 5523.523666]     invalid access to FAT (entry 0x1ac0be6f)
[ 5523.523888] FAT: Filesystem panic (dev sdc1)
[ 5523.523891]     invalid access to FAT (entry 0x28886650)
[23296.879438] usb 1-3: USB disconnect, address 4
[31554.648712] mmc0: new high speed SDHC card at address b368
[31554.653083] mmcblk0: mmc0:b368 LEXAR 3.72 GiB 
[31554.653180]  mmcblk0: p1
[31562.696255] FAT: Filesystem panic (dev mmcblk0p1)
[31562.696263]     invalid access to FAT (entry 0x7ad9f3bd)
[31562.696270]     File system has been set read-only
[31562.696832] FAT: Filesystem panic (dev mmcblk0p1)
[31562.696839]     invalid access to FAT (entry 0x4d5ec21f)
[31582.148707] FAT: Filesystem panic (dev mmcblk0p1)
[31582.148717]     invalid access to FAT (entry 0x7ad9f3bd)
[31582.149360] FAT: Filesystem panic (dev mmcblk0p1)
[31582.149372]     invalid access to FAT (entry 0x4d5ec21f)
[31582.151171] FAT: Filesystem panic (dev mmcblk0p1)
[31582.151180]     invalid access to FAT (entry 0xa483408c)
[31582.151941] FAT: Filesystem panic (dev mmcblk0p1)
[31582.151948]     invalid access to FAT (entry 0x235ef2eb)
[31582.152251] FAT: Filesystem panic (dev mmcblk0p1)
[31582.152261]     invalid access to FAT (entry 0xc22eb298)
[31582.153116] FAT: Filesystem panic (dev mmcblk0p1)
[31582.153127]     invalid access to FAT (entry 0x1ac0be6f)
[31582.153527] FAT: Filesystem panic (dev mmcblk0p1)
[31582.153537]     invalid access to FAT (entry 0x28886650)
[31594.620296] FAT: Filesystem panic (dev mmcblk0p1)
[31594.620306]     invalid access to FAT (entry 0x7ad9f3bd)
[31594.620635] FAT: Filesystem panic (dev mmcblk0p1)
[31594.620641]     invalid access to FAT (entry 0x4d5ec21f)
cygoku@shizzled:~$ 

...

Cygoku

---

### Post by dcstar on 2009-08-16
> **Cygoku said:**
> There it is :

cygoku@shizzled:~$ dmesg | tail -30
[ 5523.523666]     invalid access to FAT (entry 0x1ac0be6f)
[ 5523.523888] FAT: Filesystem panic (**dev sdc1**)
[ 5523.523891]     invalid access to FAT (entry 0x28886650)
[23296.879438] usb 1-3: USB disconnect, address 4
[31554.648712] mmc0: new high speed SDHC card at address b368
[31554.653083] mmcblk0: mmc0:b368 LEXAR 3.72 GiB 
[31554.653180]  mmcblk0: p1
.......
[31594.620635] FAT: Filesystem panic (dev mmcblk0p1)
[31594.620641]     invalid access to FAT (entry 0x4d5ec21f)
cygoku@shizzled:~$ 

...

Cygoku

Do a fsck on the filesystem.

---

### Post by Cygoku on 2009-08-16
Here is the output for my # sudo fsck /dev/sdc1

cygoku@shizzled:~$ sudo fsck /dev/sdc1
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext2: No such file or directory while trying to open /dev/sdc1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

cygoku@shizzled:~$ 

... I think there is something wrong.  

Cygoku

---

### Post by Cygoku on 2009-08-16
Hello ??

---

### Post by tgalati4 on 2009-08-16
Well, fsck is supposed to automatically detect the filesystem type.  Try:

sudo fsck.vfat /dev/sdc1

---

### Post by Cygoku on 2009-08-17
Can  simply format it ?? If Yes, how ?? 

Cygoku

---

### Post by fragos on 2009-08-17
Is your card SDHC and over 2GB? I've had no problem with SD cards 2GB and smaller. I purchased an 8GB SDHC card and it responds as Read only. One difference is the SDHC card uses FAT32 and the SD uses FAT16. The same problem came up when using the SDHC card with my Nokia N810 which is also Linux but on an ARM processor. Both systems work as expected with plain SD cards formated to FAT16.

---

### Post by tgalati4 on 2009-08-17
Format the card in Windows, or a camera, or some device that has format capability.  You can format in FAT16 or FAT32 in linux, but you must use the proper heads, cylinders, sectors count for the card.  If you don't, then the card won't work properly.  As I discovered with my 2 GB SD cards on my nokia n800.

Linux trys to format it using rational counts, but they are appropriate for real hard disks, not flash cards.

So, yes, if you have the data off the card, then by all means format it anyway you can.

---

