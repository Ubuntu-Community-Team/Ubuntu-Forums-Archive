---
title: "Setting permissions for read/write access"
date: 2006-06-17
forum: General Help
---

### Post by sabredog on 2006-06-17
Just set up a new 40Gb external drive, partitioned into 2x20Gb Fat32 drives.

How can I set up permissions to enable me to read/write successfully using such programmes as Azureus, which only allows a file creation on my home area, disallowing file creation on other drives?

cheers and thanks

---

### Post by mlind on 2006-06-17
[https://wiki.ubuntu.com/MountingWindowsPartitions](https://wiki.ubuntu.com/MountingWindowsPartitions)
That umask param sets the read/write permissions

---

### Post by sabredog on 2006-06-17
[QUOTE=mlind][https://wiki.ubuntu.com/MountingWindowsPartitions](https://wiki.ubuntu.com/MountingWindowsPartitions)
That umask param sets the read/write permissions[/QUOTE]

That does help thanks.

Ok, some more info...

2x20Gb internal drives, one is a windows XP drive and the other is my Ubuntu drive, partitioned into Ubuntu, swap and a 10GB FAT32 partition.

I have added a 40GB external drive via USB partitioned into 2x 20Gb FAT32 partitions.

I can file create using Azureus for example within my home folder but not on the 10GB FAT32 partitions or the two 20Gb externals. File transfer and access is fine on all.

I am sure it is something to do with permissions and I really would like FULL file creation access not transfer permissions only.

Hope that helps explain a little better.

I did not think that external drives would be part of the *fstab* drive list?

cheers and thanks

---

### Post by mlind on 2006-06-17
[QUOTE=sabredog]That does help thanks.

Ok, some more info...

2x20Gb internal drives, one is a windows XP drive and the other is my Ubuntu drive, partitioned into Ubuntu, swap and a 10GB FAT32 partition.

I have added a 40GB external drive via USB partitioned into 2x 20Gb FAT32 partitions.

I can file create using Azureus for example within my home folder but not on the 10GB FAT32 partitions or the two 20Gb externals. File transfer and access is fine on all.

I am sure it is something to do with permissions and I really would like FULL file creation access not transfer permissions only.

Hope that helps explain a little better.

I did not think that external drives would be part of the *fstab* drive list?

cheers and thanks[/QUOTE]


How does your new FAT partitions look on /etc/mtab when you plug your USB drive in ? 

I think gnome-volume-manager automatically mounts these as read-only, but
you must override this using /etc/fstab

---

### Post by sabredog on 2006-06-18
[QUOTE=mlind]How does your new FAT partitions look on /etc/mtab when you plug your USB drive in ? 

I think gnome-volume-manager automatically mounts these as read-only, but
you must override this using /etc/fstab[/QUOTE]

```
/dev/hdc2 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
lrm /lib/modules/2.6.15-25-386/volatile tmpfs rw 0 0
/dev/hda1 /media/windows ntfs rw,nls=utf8,umask=0222 0 0
/dev/hdc1 /media/documents vfat rw,umask=000 0 0
/dev/hdb /media/cdrom0 iso9660 ro,noexec,nosuid,nodev,user=madmike 0 0
/dev/hdd /media/cdrom1 iso9660 ro,noexec,nosuid,nodev,user=madmike 0 0
/dev/sdd1 /media/EXTERNAL-01 vfat rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0
/dev/sdd2 /media/EXTERNAL-02 vfat rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0
```

This is the contents of mtab.

What needs to be altered?

cheers and thanks

---

### Post by mlind on 2006-06-18
[QUOTE=sabredog]```
/dev/hdc2 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
lrm /lib/modules/2.6.15-25-386/volatile tmpfs rw 0 0
/dev/hda1 /media/windows ntfs rw,nls=utf8,umask=0222 0 0
/dev/hdc1 /media/documents vfat rw,umask=000 0 0
/dev/hdb /media/cdrom0 iso9660 ro,noexec,nosuid,nodev,user=madmike 0 0
/dev/hdd /media/cdrom1 iso9660 ro,noexec,nosuid,nodev,user=madmike 0 0
/dev/sdd1 /media/EXTERNAL-01 vfat rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0
/dev/sdd2 /media/EXTERNAL-02 vfat rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0
```

This is the contents of mtab.

What needs to be altered?

cheers and thanks[/QUOTE]

These look like your two FAT32 partitions on a extenal drive
```

/dev/sdd1 /media/EXTERNAL-01 vfat rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0
/dev/sdd2 /media/EXTERNAL-02 vfat rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0

```

You said that you can't write on /media/EXTERNAL-01 or 02? To me that umask
attribute looks like you should have read/write/execution permissions, but group
and others not..

Whats the output of 
```

touch /media/EXTERNAL-01/test.tmp
ls -la test.tmp

```

I know how to write a udev rule to your device that would always mount partitions
on their own nodes, but I think gnome-volume-manager should mount this on
read/write mode.

---

### Post by sabredog on 2006-06-18
I can read and write to those drives using Nautilus, but if I try and save to those drives using Azureus or OO, I cannot. Azureus gives a permissions error and OO simply does not do a thing.

To top this off, my Nvidia vidcard died :(

cheers and thanks

---

