---
title: "Mount / Fdisk  help request"
date: 2009-08-10
forum: General Help
---

### Post by hotpuppy on 2009-08-10
Hello,
  I am working on a server project and find that the mount commands output on Ubuntu Server (Jaunty) is a bit challenging to reconcile.  Perhaps someone has some suggestions to help.
 
Background:
I am building 3 servers as part of an offsite mirroring project using rsync.  The challenge is that one of the boxes failed a torture test last week.  When we simulated remote abuse (unplug without shutdown) the system crashed and didn't come back up.  We recieved a kernel panic on that machine.  Subsequent investigation suggests that the offending partition was running EXT2 and that perhaps EXT3 would be more reliable.
 
The servers are connected to a small UPS capable of sustaining them for over 10 minutes.  However, the boxes will be in remote locations where someone might accidentally unplug them or do other evil.  I'm trying to ensure that they are as bullet proof as possible.  I'm more concerned with data reliability then I am with speed as each remote mirror will be accessed via a VPN link which is slower than any ethernet connection or hard drive.
 
Hardware Config:
Intel Atom N330 dual core processor w/ 1GB of Ram
1 TB Sata drive
integrated Ethernet
No CD and monitor and keyboard stay disconnected.
fyi these machines draw a peak 60 watt load and the load is often near 45 watts.
 
Following the default server install the installer partitions the drive into 3 partitions. A swap, what appears to be a data and what appears to be an OS.  
 
Because fstab uses UUID's it's a bit confusing to compare against mount and fdisk.
 
Fdisk makes the most sense, clearly identifying the partitions.  I understand that the UUID is more reliable in /etc/fstab..... and that's good.  I'm just having a hard time tracing if my data partition is mounted as EXT2.
 
Using fdisk -l returns:
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000da45e
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      121570   976510993+  8e  Linux LVM
/dev/sda2          121571      121601      249007+   5  Extended
/dev/sda5          121571      121601      248976   83  Linux

 
 
df -h returns: 
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/eaback-root
                      911G   63G  802G   8% /
tmpfs                1002M     0 1002M   0% /lib/init/rw
varrun               1002M  300K 1002M   1% /var/run
varlock              1002M     0 1002M   0% /var/lock
udev                 1002M  132K 1002M   1% /dev
tmpfs                1002M     0 1002M   0% /dev/shm
lrm                  1002M  2.2M 1000M   1% /lib/modules/2.6.28-14-server/volatile
/dev/sda5             228M   27M  190M  13% /boot
 
mount returns
/dev/mapper/eaback-root on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-14-server/volatile type tmpfs (rw,mode=755)
/dev/sda5 on /boot type ext2 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)

when I look at /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/mapper/eaback-root during installation
UUID=d3b0181c-6479-430b-8e2f-ce462338d1a8 /               ext3    relatime,errors=remount-ro 0       1
# /boot was on /dev/sda5 during installation
UUID=1f4c6459-2ca3-4ff3-9f7c-9855e9471944 /boot           ext2    relatime        0       2
# swap was on /dev/mapper/eaback-swap_1 during installation
UUID=b5c42986-6c30-48d2-ab63-582a32b088c0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
 
 
I'm having a difficult time figuring out if my main partition is mounted as EXT2.  
 
Question:
1) Is there a way to make mount put out something more readable that links the fdisk partitions to what's mounted?  
2) Am I just missing something here.... I am not an advanced Linux user, but I am an experienced IT person.  I'm in the process of moving some things to Linux from Windows.  Ubuntu is the most straightforward distro I've seen to date.  I also have some experience with Debian, Voyager, and Puppy Linux.
 
 
 
I appreciate any responses.
Best Regards,
Brian

---

### Post by quixote on 2009-08-11
The only way I've found to make sense of the varied linux partition designations is by size.  Kind of a kludge, but it usually works.

As far as I can see there's a vast main partition, /dev/sda1, which is also the first UUID listed in your fstab, that has pretty much everything on it except /boot.  It's ext3.

/dev/sda5/, which is the second UUID in fstab, contains /boot, and is formatted ext2.  

I think you could copy the files off /boot, reformat just that partition as ext3, and move the files back on.

(If you decide to go ahead and redo the whole drive, one thing I've found very useful is to have /home on a separate partition.  Then if you need to reinstall, the users' data doesn't need to be touched.)

---

### Post by dcstar on 2009-08-11
> **hotpuppy said:**
> 
.........
I'm having a difficult time figuring out if my main partition is mounted as EXT2.  
 
Question:
1) Is there a way to make mount put out something more readable that links the fdisk partitions to what's mounted?  


```
ls -al /dev/disk/by-uuid
```

---

