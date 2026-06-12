---
title: "long boot time?"
date: 2012-01-21
forum: General Help
---

### Post by funkypotatoe on 2012-01-21
Hi, is it normal when between mounting sda5 and swap partitions there is 30 seconds "pause" ?

```
[    2.980015]    generic_sse:  8436.000 MB/sec
[    2.980040] xor: using function: generic_sse (8436.000 MB/sec)
[    2.980668] device-mapper: dm-raid45: initialized v0.2594b
[    3.443049] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   33.221977] Adding 2046972k swap on /dev/sdb6.  Priority:-1 extents:1 across:2046972k 
[   33.226969] udevd[458]: starting version 173
[   33.265492] lp: driver loaded but no devices found
[   33.307183] i2c i2c-0: nForce2 SMBus adapter at 0x600
[   33.307221] i2c i2c-1: nForce2 SMBus adapter at 0x700
[   33.341563] wmi: Mapper loaded
[   33.387118] parport_pc 00:05: reported by Plug and Play ACPI

```

---

### Post by raja.genupula on 2012-01-21
actually the primary and default reason for long boot is high list of start up programs , so remove unnecessary programs from the list.

All the best.

---

### Post by funkypotatoe on 2012-01-21
Isn't it too early for startup programs ?

---

### Post by raja.genupula on 2012-01-21
Hi , give me the output of /etc/fstab.

---

### Post by funkypotatoe on 2012-01-21
> **raja.genupula said:**
> Hi , give me the output of /etc/fstab.

```
*@*:~$ cat /etc/fstab
# /etc/fstab: static file system information.
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=52f80f98-44d7-4fa9-a279-0213fe67e64b /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda3 during installation
UUID=1527dd7d-173b-4152-b77a-fc2fc646caf1 /boot           ext2    defaults        0       2
# /home was on /dev/sda6 during installation
UUID=a4a321cb-6bde-4c1c-93bc-3176b46dbcfc /home           ext4    defaults,user_xattr        0       2
# swap was on /dev/sdb6 during installation
UUID=147c7f0f-528d-4ba2-854e-50a9dd362656 none            swap    sw              0       0
# Downloads
/dev/sdb7	/home/*/Downloads			ext4	defaults	0	2
# Music
/dev/sdb5	/home/*/Music			ext4	defaults	0	2

```

---

### Post by raja.genupula on 2012-01-21
Hi honestly i am unable to figure out whats the issues behind this . please wait for expert eye on this . I am sorry man , i have tried to help you but i cant make it . :(

---

### Post by funkypotatoe on 2012-01-21
> **raja.genupula said:**
> Hi honestly i am unable to figure out whats the issues behind this . please wait for expert eye on this . I am sorry man , i have tried to help you but i cant make it . :(

Thanks anyway )

---

