---
title: "Unable to mount drive at start up"
date: 2011-12-07
forum: General Help
---

### Post by t-a-s on 2011-12-07
I have recently installed 11.10 alongside windows 7 (both fresh installs) and have the hard drive partitioned as follows:

1:Windows 7 (NTFS - 250GB)
2:No OS (110GB)
3:Ubuntu 11.10 (ext4 - 125GB)

I wanted partition 2 set up as a common file store that both Ubuntu and Windows could access. Initially partition 2 was formatted as FAT32 as I couldn't see an option to format it as NTFS when I installed Ubuntu.

I immediately ran in to trouble though due to the size of some of the files I wanted to to store, so I reformatted the the partition to NTFS (using windows) and it now all works a dream.

The problem I have is when I load Ubuntu it is looking for the FAT 32 drive to mount (which obviously no longer exists). It gives me the option to locate it manually or skip and continue to load (which it does and everything else is fine). So I am hoping someone on here can tell me how to update the start up configuration to remove the command to mount the old FAT32 partition.

Please let me know if I have missed anything or you need more info - although I have used the forums in the past to solve other issues this is the first time I have posted.

---

### Post by Morbius1 on 2011-12-07
Please post the output of the following commands:
```
cat /etc/fstab
```
```
sudo blkid -c /dev/null
```

---

### Post by t-a-s on 2011-12-07
Thanks for the reply, here are the outputs:

> ```
cat /etc/fstab
```

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=4eaf15bf-93b6-4094-96be-188108400f3d /               ext4    errors=remount-ro 0       1
# /windows was on /dev/sda6 during installation
UUID=E0C0-C867  /windows        vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda5 during installation
#UUID=dc60eff4-af33-4e9e-a14b-a543f2141d94 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

```

> ```
sudo blkid -c /dev/null
```

```
/dev/sda1: LABEL="System Reserved" UUID="2EE053C1E0538DC9" TYPE="ntfs" 
/dev/sda2: UUID="46FA7BF7FA7BE19B" TYPE="ntfs" 
/dev/sda4: UUID="4eaf15bf-93b6-4094-96be-188108400f3d" TYPE="ext4" 
/dev/sda6: UUID="3012DCD612DCA1E0" TYPE="ntfs" 
/dev/mapper/cryptswap1: UUID="64673bef-2c46-4340-bdaa-42afba8f5343" TYPE="swap"
```

---

### Post by Morbius1 on 2011-12-07
* If you currently have the partition mounted unmount it.

* Edit fstab as root:
```
gksu gedit /etc/fstab
```* Change this line:
>  UUID=E0C0-C867  /windows        vfat    utf8,umask=007,gid=46 0       1To this:
```
UUID=3012DCD612DCA1E0 /windows ntfs defaults,nls=utf8,umask=007,gid=46,windows_names 0 0 
```Then save the file.

* In a terminal run the following command that will test for errors and if there are none mount the partition without requiring a reboot:
```
sudo mount -a
```

---

### Post by t-a-s on 2011-12-07
Yeah, that's got it! Thank you very much!

---

