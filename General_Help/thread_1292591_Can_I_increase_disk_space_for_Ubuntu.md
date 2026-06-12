---
title: "Can I increase disk space for Ubuntu?"
date: 2009-10-16
forum: General Help
---

### Post by Tapas Bose, India on 2009-10-16
Hallo everybody.
I have Ubuntu allocated 40GB disk space. I want to increase space for Ubuntu. After googling I found that gparted will help me to do this job. I opened gparted, but it show me that I have entire HDD as unallocated disk. I can not understand this output.
The result of the command:
> sudo fdisk -lu /dev/sda
is:
> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x31a431a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    81920159    40960048+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2        81920222   312576704   115328241+   f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3       223689123   308849624    42580251   83  Linux
Partition 3 does not end on cylinder boundary.
/dev/sda5        81920285   143367839    30723777+   7  HPFS/NTFS
/dev/sda6       143367903   184327919    20480008+   7  HPFS/NTFS
/dev/sda7       184327983   204800399    10236208+   7  HPFS/NTFS
/dev/sda8       204800463   223685279     9442408+   7  HPFS/NTFS
Please help me to increase space. Waiting for reply.

Note: The screenshot of gparted is given as attachment

---

### Post by mike555 on 2009-10-16
You can not change a partition that is mounted or running , you need to use a "live" cd , ether Ubuntu or Parted Magic cd ........

---

### Post by Tapas Bose, India on 2009-10-16
> **mike555 said:**
> You can not change a partition that is mounted or running , you need to use a "live" cd , ether Ubuntu or Parted Magic cd ........
Thank you for reply. Can you please tell me how can I increase volume using LiveCD? And what about the gparted's display?

---

### Post by mocoloco on 2009-10-16
It's true you can't modify the partitions while they're mounted and in use, but gparted should still show them correctly. You probably have something wrong in your partition table. I had the same problem several months ago, and didn't spend too much time researching it because I was planning to reformat anyway, and that fixed it.  I'm sure it's fixable thought without formatting, although having a backup would be a good idea. Sorry I can't tell you how to fix it but start searching for info on problems with a partition table.

---

### Post by Tapas Bose, India on 2009-10-16
> **mocoloco said:**
> It's true you can't modify the partitions while they're mounted and in use, but gparted should still show them correctly. You probably have something wrong in your partition table. I had the same problem several months ago, and didn't spend too much time researching it because I was planning to reformat anyway, and that fixed it.  I'm sure it's fixable thought without formatting, although having a backup would be a good idea. Sorry I can't tell you how to fix it but start searching for info on problems with a partition table.
Formating of whole HDD or formating the Ubuntu? I have Vista and Ubuntu. Does formating can resolve the problem?

---

### Post by P4man on 2009-10-16
did you do a wubi install ?

---

### Post by Tapas Bose, India on 2009-10-16
> **P4man said:**
> did you do a wubi install ?
No. I don't have wubi.

---

### Post by Tapas Bose, India on 2009-10-16
> **P4man said:**
> did you do a wubi install ?
No. I don't have wubi.

---

### Post by brallan on 2009-10-16
hmmmm. judging by the output of fdisk, I think first you should use windows if possible to check your partition. I say that because ntfs partitions are probably best troubleshot from within windows. I think there's something wrong with it, because even if they are mounted (which they probably aren't if I understood correctly) gparted should still recognize the partitions correcty, unless they have some errors.

you can check to see if a partition is mounted using```
mount
```

The above post was telling you how to run from a live CD. If you need to reboot using the live CD, it may require getting into the BIOS. most modern computers should offer you a boot menu if you press escape or f8 or f10 or f12. If not, usually you can press (while booting) f2 or del or esc to get into the bios.

---

### Post by Tapas Bose, India on 2009-10-16
The output of
> mount
is
> /dev/sda3 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sda5 on /media/Movies type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

Now what to do?

---

### Post by P4man on 2009-10-16
clearly there is something wrong with his partitioning. There are 8 partitions, and none of them extended. You can only have 4 primary partitions per drive (one of which better be an extended partition, that you can further divide into logical partitions).

---

### Post by Tapas Bose, India on 2009-10-16
I have 5 partition in my vista.

---

### Post by Tapas Bose, India on 2009-10-16
Do I format my entire HDD and install Windows first and then Ubuntu?

---

### Post by mdurham on 2009-10-16
> **Tapas Bose, India said:**
> Do I format my entire HDD and install Windows first and then Ubuntu?

Yes, that's the correct order to do things BUT FIX the partitions, don't just format them.

---

### Post by Tapas Bose, India on 2009-10-16
> **mdurham said:**
> Yes, that's the correct order to do things BUT FIX the partitions, don't just format them.
Can you please tell me how can I fix the pertitions?

---

### Post by mdurham on 2009-10-16
> **Tapas Bose, India said:**
> Can you please tell me how can I fix the pertitions?

brallan in a previous post suggested having a look from Windows as it might be better for fixing NTFS partitions. There is also a "System rescue" C/D that's free which could probably sort it all out. See [http://distrowatch.com/]("http://distrowatch.com/") to find it.
Cheers, Mike

---

### Post by mocoloco on 2009-10-16
By reinstalling everything that will fix the partitions, Windows which will be installed first will see an empty drive, and will create new partitions and a new partition table.  When you install windows, just let it format the whole drive and make it's own partitions.  That's how I fixed it on my system.  Still not sure what ever cause the problem but it's been fine ever since, about 6 months now.

---

