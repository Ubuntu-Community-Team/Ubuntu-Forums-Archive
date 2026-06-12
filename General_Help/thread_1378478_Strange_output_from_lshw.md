---
title: "Strange output from lshw"
date: 2010-01-11
forum: General Help
---

### Post by coldraven on 2010-01-11
This is a fresh install of Ubuntu 9.10 64bit on a Compaq 6715b laptop.
Everything is working OK except the fingerprint reader.
So to look for the device I did this:
```
sudo lshw
```but was a bit alarmed when I saw this:

*-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 92b1bba9-74a3-4af3-8708-515fa76cac56
                   size: 142GiB
                   capacity: 142GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-01-07 22:51:18 filesystem=ext4 lastmountpoint=/h}.&#65533;&#65533;&#65533;&#65533;&#65533;]u8}.&#65533;&#65533;&#65533;&#65533;7&#65533;&#65533;&#65533;&#65533;5&#65533;&#65533;&#65533;@8&#65533;/&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#1118;6&#65533; modified=2010-01-07 23:35:33 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-01-11 17:48:52 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 6236MiB
                   capacity: 6236MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 6236MiB
                      capabilities: nofs

What is the cause of the strange characters?
Is my hard drive dying?

---

### Post by philinux on 2010-01-11
> **coldraven said:**
> This is a fresh install of Ubuntu 9.10 64bit on a Compaq 6715b laptop.
Everything is working OK except the fingerprint reader.
So to look for the device I did this:
```
sudo lshw
```but was a bit alarmed when I saw this:

*
                   configuration: created=2010-01-07 22:51:18 filesystem=ext4 lastmountpoint=/h}.&#65533;&#65533;&#65533;&#65533;&#65533;]u8}.&#65533;&#65533;&#65533;&#65533;7&#65533;&#65533;&#65533;&#65533;5&#65533;&#65533;&#65533;@8&#65533;/&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#1118;6&#65533; modified=2010-01-07 23:35:33 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-01-11 17:48:52 state=mounted

```
configuration: created=2009-11-03 16:15:50 filesystem=ext4 label=Root lastmountpoint=/&#65533;;Cp&#65533;&#65533;&#65533;u&#65533;5<&#65533;;Cp&#65533;&#65533;&#65533;&#65533;r{&#65533;&#65533;&#65533;&#65533;)I}&#65533;&#65533;&#65533;&#65533;x&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#1567;&#65533;y&#65533; modified=2009-12-11 13:40:06 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-01-10 20:01:23 state=mounted
```

Same here, dont know why. But my system is running fine. I suspect lshw hasn't been tweaked for ext4 or something like that.

---

### Post by coldraven on 2010-01-11
Thanks Philinux :wink:

---

