---
title: "Share local disk on desktop"
date: 2011-03-05
forum: General Help
---

### Post by jabog6 on 2011-03-05
Hi,

If the answer to this question is available elsewhere, my apologies.  I searched...

I installed Ubuntu 10.10 (64 bit) on a Dell Precision 670 desktop that I share with another user.  The OS is installed on a 160GB disk, which also has the /home folders.  There is also a second internal disk (1TB) which has shared files (music, pictures, etc).  

How can I configure Ubuntu such that either person can read or write to this shared disk?  Right now, if someone is logged into the PC, the disk can be mounted, but then it is not available to the other person.

Any help would be appreciated.

---

### Post by seawolf167 on 2011-03-05
Welcome to the forums!

If you add an entry for that hard drive in /etc/fstab it'll be mounted at boot as root, then you should only have to worry about having the correct file/folder permissions for the users/groups.

See the link in my sig for more fstab info, or I can help if you post the output to

```
blkid
sudo fdisk -l
mount
```

---

### Post by jabog6 on 2011-03-06
Hi seawolf167,

Thanks for offering to help.  I appreciate it.  

blkid does not return anything.

sudo fdisk -l returns:
```
Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb7ff2d40

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    7  HPFS/NTFS

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000f1ad

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18708   150268928   83  Linux
/dev/sda2           18708       19458     6019073    5  Extended
/dev/sda5           18708       19458     6019072   82  Linux swap / Solaris
```mount returns:
```
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /var/lib/ureadahead/debugfs type debugfs (rw,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdb1 on /media/Data type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
gvfs-fuse-daemon on /home/rick/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=rick)
```
Thanks again. :)

Added the following line to /etc/fstab:

```
/dev/sdb1       /media/Data     ntfs    
```

Seems to be working.  It was easier than I thought, once I knew where to look. :)

Thanks again.

---

### Post by seawolf167 on 2011-03-06
To fully qualify the device, change that line to this:

```
/dev/sdb1   /media/Data    ntfs-3g defaults,locale=en_US.utf8
```

to use blkid, you'll have to add a sudo in front of it, i.e.

```
sudo blkid
```

this would give you the drive's unique UUID to enter instead of the /dev/sdb1 line, but either works just fine.

```
UUID=*youruuidhere*   /media/Data    ntfs-3g defaults,locale=en_US.utf8
```

---

### Post by jabog6 on 2011-03-06
sudo blkid returns
```
/dev/sdb1: LABEL="Data" UUID="AA807F79807F4AB9" TYPE="ntfs" 
/dev/sda1: UUID="0580f83c-973b-4a41-8b3a-f35042adc9fe" TYPE="ext4" 
/dev/sda5: UUID="bc0e0bd1-cda9-424b-9401-ecad5fa7804c" TYPE="swap" 
```

So my new line entry in /etc/fstab is 
```
UUID=AA807F79807F4AB9     /media/Data     ntfs-3g defaults,locale=en_US.utf8
```

Thanks for helping a newbie. :D

---

