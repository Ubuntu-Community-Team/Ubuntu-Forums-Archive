---
title: "Error mounting: mount exited with exit code 1"
date: 2010-07-05
forum: General Help
---

### Post by hundred1906 on 2010-07-05
Two of my three internal drives no longer mount. They were there OK a couple of days ago but although visibly present in the "Computer - File Browser" window they refuse to mount and all get get is an error box with the title as above. sda is OK, it is sdb and sdc that are missing.

Text in the box says (for sdc) Error mounting: mount exited with exit code 1: helper failed with:
mount: mount point /media/Important does not exist

FSTAB is unchanged as listed below and used to happily auto mount all the drives. I am running 9.04 and the only change I am aware of is an auto update to the system (I think the update was to do with SUDO).

I see this has been reported before but I cannot see any examples covering internal drives where the problem has been solved.

All drives are present when I use an 8.04 Live Distro.

Any help is welcome.

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=7f93bb78-880c-4a24-9969-a24c8959e86b /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f4a7d076-1c9b-490d-9897-51748aab4ed8 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
UUID=a6d346ab-4818-4f42-83e1-f5da74108ab1 /media/Recordings ext3 relatime,user 0 2
UUID=63c60022-5164-4dd2-8444-08e6f6e6d3cc /media/Important ext3 relatime,user 0 2

---

### Post by CharlesA on 2010-07-05
Please post the output of this:

```
sudo fdisk -l
```

---

### Post by hundred1906 on 2010-07-06
Thanks - fdisk output is below. All the raid/solaris stuff on sda is to do with previous use as a windows disk.

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x39ee39ed

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19556   157083538+  fd  Linux RAID autodetect
/dev/sda2           19557       19929     2996122+   5  Extended
/dev/sda5           19557       19929     2996091   82  Linux swap / Solaris

Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x19f319f2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19929   160079661   83  Linux

Disk /dev/sdc: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x333eed9d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19929   160079661   83  Linux

---

### Post by hundred1906 on 2010-07-07
Any clues anyone?

---

### Post by hundred1906 on 2010-07-07
By removing the last two lines in the FSTAB file I can at least mount the drives manually as Root. What is that telling me?

---

### Post by hundred1906 on 2010-07-08
When I put back the two lines the problem returns. Looking into the Nautilus File browser into /media there is a folder entry for "disk" with a big cross against the symbol that generally does not look like a good sign. My two drives only appear in /Media if I manually mount them and they are not specified in FSTAB.

---

### Post by Morbius1 on 2010-07-08
> UUID=a6d346ab-4818-4f42-83e1-f5da74108ab1 /media/Recordings ext3  relatime,user 0 2
UUID=63c60022-5164-4dd2-8444-08e6f6e6d3cc /media/Important ext3  relatime,user 0 2> mount: mount point /media/Important does not existFor starters make sure the UUID numbers are correct by issuing the following command and checking it by hand:
```
sudo blkid -c /dev/null
```Make sure the mount points actually exist. If they do not then create them:
```
sudo mkdir /media/Important
sudo mkdir /media/Recordings
```

---

### Post by hundred1906 on 2010-07-09
OK, thanks. Creating the mount points as you described seems to have fixed it. Funny though as I do not recall needing to do that in the first place. Plus why did the mount points disappear at all?
Nevermind.

---

