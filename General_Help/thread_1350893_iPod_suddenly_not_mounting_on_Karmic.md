---
title: "iPod suddenly not mounting on Karmic"
date: 2009-12-09
forum: General Help
---

### Post by Cal27 on 2009-12-09
Today, I heard about Yamipod and decided to give it a try. Upon connecting my iPod, I found that it would not auto-mount as usual. The iPod shows the usual 'Connected' screen, but it doesn't show up in /media/ or on the desktop. I've been using my iPod without problems on Ubuntu for about 6 months; I just connected it without problems yesterday (or perhaps the day before). The only changes I've made since then are installing the new version of Thunderbird and downloading Yamipod, which is a standalone binary aside from the libraries (libfmodex.so.4.02.05 and libstdc++5), but I believe I have ruled out those. My iPod appears to be working fine [when not connected] and it will still connect, but not mount.

It shows up on lsusb:
```
Bus 001 Device 014: ID 05ac:1261 Apple, Inc. iPod Classic
```and lshw:
```
 *-disk
       description: SCSI Disk
       product: iPod
       vendor: Apple
       physical id: 0.0.0
       bus info: scsi@12:0.0.0
       logical name: /dev/sde
       version: 1.62
       serial: -----------
       size: 74GiB (79GB)
       capabilities: removable
     *-medium
          physical id: 0
          logical name: /dev/sde
          size: 74GiB (79GB)
          capabilities: partitioned partitioned:dos
          configuration: signature=20202020

```I tried to mount it and came up with this (I probably did it wrong, or at least I hope I did):
```

$ sudo mount /dev/sde /media/iPod
mount: wrong fs type, bad option, bad superblock on /dev/sde,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```dmesg | tail
```

$ dmesg | tail
[263612.573315] sd 12:0:0:0: [sde] Mode Sense: 68 00 00 08
[263612.573321] sd 12:0:0:0: [sde] Assuming drive cache: write through
[263612.581471] sd 12:0:0:0: [sde] 19488471 4096-byte logical blocks: (79.8 GB/74.3 GiB)
[263612.582499] sd 12:0:0:0: [sde] Assuming drive cache: write through
[263612.582517]  sde: sde1
[263612.602491] sd 12:0:0:0: [sde] 19488471 4096-byte logical blocks: (79.8 GB/74.3 GiB)
[263612.606197] sd 12:0:0:0: [sde] Assuming drive cache: write through
[263612.606209] sd 12:0:0:0: [sde] Attached SCSI removable disk
[264039.307912] FAT: count of clusters too big (4871989)
[264039.307921] VFS: Can't find a valid FAT filesystem on dev sde.

```Hope all that will be useful. Any help is greatly appreciated :)

---

### Post by audiomick on 2009-12-09
I know it is not much help, but I think you are not the only one having trouble with the iPod with 9.10

---

### Post by Cal27 on 2009-12-09
Well, at least I know I'm not the only one. And my iPod is probably not broken.

---

### Post by Vishnu V on 2009-12-10
> **Cal27 said:**
> Today, I heard about Yamipod and decided to give it a try. Upon connecting my iPod, I found that it would not auto-mount as usual. The iPod shows the usual 'Connected' screen, but it doesn't show up in /media/ or on the desktop. I've been using my iPod without problems on Ubuntu for about 6 months; I just connected it without problems yesterday (or perhaps the day before). The only changes I've made since then are installing the new version of Thunderbird and downloading Yamipod, which is a standalone binary aside from the libraries (libfmodex.so.4.02.05 and libstdc++5), but I believe I have ruled out those. My iPod appears to be working fine [when not connected] and it will still connect, but not mount.

It shows up on lsusb:
```
Bus 001 Device 014: ID 05ac:1261 Apple, Inc. iPod Classic
```and lshw:
```
 *-disk
       description: SCSI Disk
       product: iPod
       vendor: Apple
       physical id: 0.0.0
       bus info: scsi@12:0.0.0
       logical name: /dev/sde
       version: 1.62
       serial: -----------
       size: 74GiB (79GB)
       capabilities: removable
     *-medium
          physical id: 0
          logical name: /dev/sde
          size: 74GiB (79GB)
          capabilities: partitioned partitioned:dos
          configuration: signature=20202020

```I tried to mount it and came up with this (I probably did it wrong, or at least I hope I did):
```

$ sudo mount /dev/sde /media/iPod
mount: wrong fs type, bad option, bad superblock on /dev/sde,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```dmesg | tail
```

$ dmesg | tail
[263612.573315] sd 12:0:0:0: [sde] Mode Sense: 68 00 00 08
[263612.573321] sd 12:0:0:0: [sde] Assuming drive cache: write through
[263612.581471] sd 12:0:0:0: [sde] 19488471 4096-byte logical blocks: (79.8 GB/74.3 GiB)
[263612.582499] sd 12:0:0:0: [sde] Assuming drive cache: write through
[263612.582517]  sde: sde1
[263612.602491] sd 12:0:0:0: [sde] 19488471 4096-byte logical blocks: (79.8 GB/74.3 GiB)
[263612.606197] sd 12:0:0:0: [sde] Assuming drive cache: write through
[263612.606209] sd 12:0:0:0: [sde] Attached SCSI removable disk
[264039.307912] FAT: count of clusters too big (4871989)
[264039.307921] VFS: Can't find a valid FAT filesystem on dev sde.

```Hope all that will be useful. Any help is greatly appreciated :)


I think there is a problem in the  command you tried to mount.
the device name not completed 
try 
```

sudo mount /dev/sde1 /media/iPod

```
here device name maynot be /dev/sde1 but any number instead of 1
it can be found out by
```

sudo fdisk -l

```

---

### Post by Cal27 on 2009-12-10
> **Vishnu V said:**
> I think there is a problem in the  command you tried to mount.
the device name not completed 
try 
```

sudo mount /dev/sde1 /media/iPod

```here device name maynot be /dev/sde1 but any number instead of 1
it can be found out by
```

sudo fdisk -l

```
Thanks, that worked great. I could have sworn I tried that too :). Now to just get my media auto-mounting again...

---

### Post by LuisGMarine on 2009-12-10
```
sudo cp /etc/fstab /etc/fstab_backup
```
```
sudo gedit /etc/fstab
```

Then add this to the file, save, and try connecting your iPod and see if it auto-mounts.
```

#Entry for iPod auto-mount
/dev/sde1 /media/iPod vfat nosuid,noauto,nodev,rw,umask=077,gid=1000,uid=1000,user,defaults,noatime,iocharset=utf8 0 0
```

---

### Post by Cal27 on 2009-12-12
Thanks for the help, but the problem has fixed itself after booting to the root console a few times, then doing a fsck at startup. All my media is auto-mounting without problems

---

### Post by nyex on 2010-03-10
> **Cal27 said:**
> Thanks for the help, but the problem has fixed itself after booting to the root console a few times, then doing a fsck at startup. All my media is auto-mounting without problems

I managed to mount my ipod with Vishnu V's help, but I would like to have it automounting again. Could you explain to me how you got it working back again? I mean, what do you mean booting to the root console and how to do a fsck at startup?? :) I know these may be dumb questions, but if you could help me, I'd be really glad :D

Regards,

---

