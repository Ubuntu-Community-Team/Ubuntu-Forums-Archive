---
title: "/home partition borked"
date: 2009-11-26
forum: General Help
---

### Post by Tiiba on 2009-11-26
I installed Karmic, played around with it, and decided that it's not ready for me-time. Too many things broken. So I decided to go back to the best Linux I ever had, Hardy. I had a partition for /home, which was ext4, which Hardy didn't support. I called it /home/extra and mounted it as ext3, without formatting. I boot up, and it's not there... I reinstall with Karmic, mounting as /home - still not there. It shows only the default folders, with nothing in them. I know the data is there, because it takes up 163 MB. How to get to it?

There are a few small files I'd give a minor organ to recover.

---

### Post by blueridgedog on 2009-11-26
I suspect the partition is there, just not mounted.  Can you post the output of:

```
mount
```

and 

```
sudo fdisk -l
```

So we can see what partitions you have and what is mounted where?

Also, do you recall what the device and number the partition was?

---

### Post by Tiiba on 2009-11-26
The partition is mounted as /home, as I described. Which means that I should probably get off this computer before I overwrite anithing else.

mount:
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda6 on /home type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/user/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=user)
/dev/sr0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=user)
/dev/sda7 on /media/f260d96b-1582-406b-b9f0-37894d71c695 type ext3 (rw,nosuid,nodev,uhelper=devkit)


fdisk -l:
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95f3457a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+  83  Linux
/dev/sda2            2433       14593    97683232+   5  Extended
/dev/sda5           14220       14593     3004123+  82  Linux swap / Solaris
/dev/sda6            6080       14219    65384487   83  Linux
/dev/sda7            5472        6079     4883728+  83  Linux
/dev/sda8            2433        5470    24402672   83  Linux

---

### Post by dcstar on 2009-11-26
> **Tiiba said:**
> I installed Karmic, played around with it, and decided that it's not ready for me-time. Too many things broken. So I decided to go back to the best Linux I ever had, Hardy. I had a partition for /home, which was ext4, which Hardy didn't support. I called it /home/extra and mounted it as ext3, without formatting. I boot up, and it's not there... I reinstall with Karmic, mounting as /home - still not there. It shows only the default folders, with nothing in them. I know the data is there, because it takes up 163 MB. How to get to it?

There are a few small files I'd give a minor organ to recover.

You can try to remove the journaling and turn it back into an EXT2 partition, or at least do an fsck on it.

---

### Post by Tiiba on 2009-11-26
Which is safer?

---

### Post by blueridgedog on 2009-11-26
So, you are certain that the partition that had the data is sda6, which is currently mounted on /home and not sda7 (mounted in the media directory) or sda8 (not mounted).

You implied that space was used on sda6.  What does 

```
df
```

show?

dcstar's suggestion is a good one, especially if you can't see files that use the space.  You may want to make a ddrescue image of the partition (if you have room) before you attempt to alter it.

---

### Post by Tiiba on 2009-11-27
df:
Filesystem           1K-blocks      Used Available Use% Mounted on
aufs                    508676     49776    458900  10% /
udev                    508676       296    508380   1% /dev
/dev/sr0                706532    706532         0 100% /cdrom
/dev/loop0              684032    684032         0 100% /rofs
none                    508676       100    508576   1% /dev/shm
tmpfs                   508676        12    508664   1% /tmp
none                    508676        88    508588   1% /var/run
none                    508676         4    508672   1% /var/lock
none                    508676         0    508676   0% /lib/init/rw
/dev/sda1             48062440   2126404  43494560   5% /media/7e2df8ca-a0c2-4893-9955-927d6e6f7757


I changed my setup again, so sda6 wouldn't be used at all. Gnome System Monitor says it has 206.8 MiB in use. (I guess I misread the number I quoted before).

I want to back it up, but it's bigger than the other partition.

---

### Post by Tiiba on 2009-11-27
I made a backup of the first few gigabytes to a file called "backup.txt" and tried to grep it, but I don't think I'm using grep right. How can I go about getting data from the file?

The only data I really care about is a program I wrote and was stupid enough not to back up, so I can expect certain phrases to occur in it. Does that do me any good?

---

### Post by dcstar on 2009-11-27
> **Tiiba said:**
> Which is safer?

Don't know, but you should always try a fsck on any potentially corrupted partition.

If you want to remove the journal (on the chance that it is bad), here is a command I found (for an unmounted partition):

```
sudo tune2fs -O ^has_journal /dev/sda-whatever
```

---

### Post by blueridgedog on 2009-11-27
Odd, though it shows it mounted, the /home mount did not show up in df.

---

