---
title: "Unmounted Drive Wont Remount"
date: 2010-05-12
forum: General Help
---

### Post by SimDendrite on 2010-05-12
I unmounted a drive using:[INDENT][FONT=Courier New]sudo umount -l /media/1f55644c-e48e-348d-ab3e-38b4ab5d9eaf[/FONT]
[/INDENT]I cant get the drive to remount, If i go to the "places" menu and select the drive it usually mounts onto the desktop but instead I get the following error:[INDENT][FONT=Courier New]Error mounting: mount: /dev/sda2 already mounted or /media/1f55644c-e48e-348d-ab3e-38b4ab5d9eaf busy[/FONT]
[/INDENT]Disk Utility shows the drive but when I click "Mount Volume" I get this error:[INDENT][FONT=Courier New]Error mounting volume
An error occurred while performing an operation on "500 GB Filesystem" (Partition 2 of ATA WDC WD5000AAKS-40TMA0): Filesystem driver not installed

Details
Error mounting: mount: /dev/sda2 already mounted or  /media/1f55644c-e48e-348d-ab3e-38b4ab5d9eaf busy
[/FONT][/INDENT]Its a HFS+ drive, but I just need to mount it to copy all the files off. The OS on the computer is destroyed so right now I booting off a 10.04 LST livecd. 

How do I make the unmounted drive not busy and then successfully remount the drive and unlock all the privileges so I can backup the files onto a usb drive?

---

### Post by CharlesA on 2010-05-12
You could try running this and seeing if the device is still mounted for some reason:

```
mount -l
```

I am not sure if this will work but it might be worth a shot:

```
lsof /dev/sdxx
```

---

### Post by SimDendrite on 2010-05-12
Thank you for the quick response, pulling my hair out trying to fix this tonight. Here is what I get trying those two commands:
[INDENT][FONT=Courier New]ubuntu@ubuntu:~$ mount -l
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sr0 on /cdrom type iso9660 (ro,noatime) [Ubuntu 10.04 LTS i386]
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb1 on /media/Backup type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions) [Backup]

ubuntu@ubuntu:~$ lsof /dev/sda2
lsof: WARNING: can't stat() tmpfs file system /cow
      Output information may be incomplete.
[/FONT][/INDENT]Is there some way that I can reload ubuntu but not lose any of the settings I have setup on the livecd before I left (such as remote desktop and the network connections)? I am at home right now and the computer is a good hour away in a empty locked building.
[INDENT][FONT=Courier New]

[/FONT][/INDENT]

---

### Post by CharlesA on 2010-05-12
If it's booted off a livecd, there's nothing you can really do to reload the OS so that it has all the settings you changed. 

What does this return?

```
sudo fdisk -l
```

---

### Post by SimDendrite on 2010-05-12
[FONT=Courier New]ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x12345678

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS[/FONT]

---

### Post by CharlesA on 2010-05-12
Hrm. There should have been a listing for sda.

Is sdb the same size as the one you are trying to pull data off of?

---

### Post by SimDendrite on 2010-05-12
Yes both drives are 500gb, I think its showing the external USB drive I plugged in to make the backup onto but not the Internal drive to copy from now.

---

### Post by CharlesA on 2010-05-12
Yeah. It doesn't see the internal drive at all.

I'm guessing sdb1 is the external drive, since it's labeled "Backup"

Best thing you could do is to shutdown the system and then bring it back up and see if Ubuntu detects all the drives.

---

### Post by SimDendrite on 2010-05-12
That's what I feared.

If I reboot it tonight I wont be able to get back on the machine until I can physically get access to it at 10am and boot from the CD, its just going to hang at boot trying to load the corrupted OSX system. Was hoping I could get this data backed up tonight and have it ready for our Production Dept. in the morning.

When I do get back on the machine, how do I go about mounting that drive again with all the privileges to copy the data?

---

### Post by CharlesA on 2010-05-12
You could probably just mount it from a root shell and copy the data over that way.

What I do for backups is use rsync:

```
rsync -ai source destination
```

Only problem with that one is that you need to run it as root to copy the permissions/owner/group over.

You can just do sudo -s to get a rootshell and go from there.

Best of luck to you.

---

