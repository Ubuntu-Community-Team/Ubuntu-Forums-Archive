---
title: "Non Clean Shutdown"
date: 2010-12-07
forum: General Help
---

### Post by Gilbuzz on 2010-12-07
Hi,

I've started getting major problems on my laptop (HP8440p). Ubuntu 10.10 64Bit

I've removed the CDrom and added an SSD disk and partitioned as follows (Pretty much based on info from the Arch Wiki):

/dev/sdb1    /       10Gig SSD
/dev/sdb2    /home   50Gig SSD
/dev/sda6    /data   300Gig SATA
/dev/sda1    /var    10Gig  SATA

I've noticed file loss recently and that my history file is very rarely persistent - Guessing that there is a Non Clean Shutdown. 

```
shutdown -h now > error.log
```

Doesn't ever capture anything and the shutdown is so quick can't read any errors..

Here is my /etc/fstab

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=2fd2c3c8-bce0-4539-9df7-d10755f230ad /               ext4    noatime,discard, errors=remount-ro 0       1
# /data was on /dev/sda6 during installation
UUID=6e32fe62-25e5-4e60-a4a8-ac3a0ffde270 /data           ext4    defaults        0       2
# /home was on /dev/sdb2 during installation
UUID=6bb140d4-8e26-4863-ba55-742d34b84caf /home           ext4    noatime,discard,defaults        0       2
# /var was on /dev/sda1 during installation
UUID=7a252ffe-7b51-4e10-ad40-2092adcb80ed /var            ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=40ab0b9c-95d9-418c-b3bf-29175322520c none            swap    sw              0       0

```

Any help in troubleshooting this would be most appreciated.

Cheers.

---

### Post by Gilbuzz on 2010-12-08
Okay try and solve this myself...


```
dmesg | grep -i recovery
[    4.034798] EXT4-fs (sdb1): INFO: recovery required on readonly filesystem
[    4.034805] EXT4-fs (sdb1): write access will be enabled during recovery
[    4.048765] EXT4-fs (sdb1): recovery complete

```

A search of this reveals this possible bug:

[https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/616287](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/616287)

Hmm...

---

