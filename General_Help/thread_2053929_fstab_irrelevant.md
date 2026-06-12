---
title: "fstab irrelevant?"
date: 2012-09-06
forum: General Help
---

### Post by grizdog on 2012-09-06
I just bought a new disk and installed it (internally) in my desktop computer, presently running ubuntu 10.04.  I partitioned it, made a filesystem, and mounted it on a temporary mount point (/media/newdrive).  Then did an df to double check, everything looked good.  Next step was to edit fstab.

The new disk is /dev/sda1.  The root partition is presently on /dev/sdb1 - based on the output of df.  But in fstab, which hasn't been modified for over a year, the root filesystem is on /dev/sda1.  I rebooted, and nothing changed.  So is fstab irrelevant?

The plan is to install the latest ubuntu on the new disk, and then copy over personal stuff from the old disk.  I could probably go ahead and just do this, but I'm wondering about fstab.  I know I should be using UUIDs, if I do that and throw out the old fstab, will everything magically work?

Thanks for any insight.

Alex

---

### Post by cortman on 2012-09-06
> **grizdog said:**
> 

The new disk is /dev/sda1.  The root partition is presently on /dev/sdb1 - based on the output of df.  But in fstab, which hasn't been modified for over a year, the root filesystem is on /dev/sda1.


This makes no sense to me at all. Check the device labels with fdisk- 

```
sudo fdisk -l
```

AFAIK the alphabetical order of devices (sda,sdb,sdc) never gets reversed like that.
And as far as your intentions, why bother running both drives at the same time anyway? Remove the old drive, put the new one in, install Ubuntu, then transfer your stuff.

---

### Post by ajgreeny on 2012-09-06
> **cortman said:**
> This makes no sense to me at all. Check the device labels with fdisk- 

```
sudo fdisk -l
```AFAIK the alphabetical order of devices (sda,sdb,sdc) never gets reversed like that.
And as far as your intentions, why bother running both drives at the same time anyway? Remove the old drive, put the new one in, install Ubuntu, then transfer your stuff.
No, fstab is certainly not irrelevant; just try booting without one and you'll see why.

I think you'll find that the sda, sdb etc, nomenclature can change in certain circumstances and that is one reason why fstab now uses UUIDs by default instead of the /dev/sda1 etc etc.

I also have no doubt that the fstab file that the OP refers to uses UUID, but mentions /dev/sdx in a commented out line above, as is the current way of doing things in Ubuntu.

If the old disk is an IDE and the new one is sata, I think that can account for the apparent reversal of priority, or the order they are attached to the cable in the machine or jumper settings of IDE disks may also be the reason.

---

### Post by Cheesemill on 2012-09-06
Can you post your fstab file please.
```
cat /etc/fstab
```

---

### Post by grizdog on 2012-09-06
Here is the output from fdisk -l:
```

sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00002b1e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121601   976760001   83  Linux

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bfb54

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29656   238209024   83  Linux
/dev/sdb2           29656       30402     5987329    5  Extended
/dev/sdb5           29656       30402     5987328   82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x61ce8b27

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   83  Linux


```And here is the content of fstab:
```

cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb1       /media/disk     ext3    rw,nosuid,nodev,uhelper=udisks   0      2


```

The drive that is mounted at /media/disk  is an external drive I use for backups.

---

### Post by grizdog on 2012-09-07
Update:  When I put in an Ubuntu install disk, the only drive it finds is the old one, the one with the old Ubuntu already installed.  It does not find the new internal disk, or the external USB disk.

Thanks for any help.  THis looks very strange to me.

---

### Post by cryptotheslow on 2012-09-07
Can you boot into the installed version and post the output of 
```
mount -l
```

It's not making sense that your fstab lists sda1 for / but fdisk shows your installation appearing to be on sdb1.

---

### Post by grizdog on 2012-09-07
Yeah, it doesn't make any sense to me either.  Here is the output from mount -l:

```

sudo mount -l
/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/alex/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=alex)
/dev/sdc1 on /media/9f6c6351-7533-4559-9099-6d148e1dc504 type ext3 (rw,nosuid,nodev,uhelper=udisks)
/dev/sda1 on /media/newdrive type ext4 (rw)


```

---

### Post by cryptotheslow on 2012-09-07
Are they both SATA disks?

---

### Post by grizdog on 2012-09-07
Yes, but the new one is plugged in to an IDE port on the motherboard, with one of those little adapter doohickies.
> **cryptotheslow said:**
> Are they both SATA disks?

---

### Post by cryptotheslow on 2012-09-07
Ah - that may well be why the installer can't recognise it.

Do you not have sufficient SATA headers for them both?

In any case if your intention is to install Ubuntu to the new disk, you could just disconnect your old drive completely and plug the new drive into the SATA header it was using. Once Ubuntu is up and running on the new disk, plug the old one in using the doohickie and copy whatever settings and files etc. across as required.

Just a suggestion based on how I'd tackle it - at least with the old drive disconnected there's no chance of accidentally overwriting your current install :D

---

### Post by grizdog on 2012-09-08
OK, I marked the thread solved, even though I still don't understand exactly why the fstab and fdisk were inconsistent, the IDE solution offered by two of you proved out.  Right now I have the dvd drive disconnected, so I'll see if it works properly with the IDE connection.  If not, I guess I'll try a sata multiplier card or maybe - just maybe - a new motherboard.

Thanks to everyone for your help.

---

