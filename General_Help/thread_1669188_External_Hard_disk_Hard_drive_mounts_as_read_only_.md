---
title: "External Hard disk /Hard drive mounts as read only (Suddenly)"
date: 2011-01-17
forum: General Help
---

### Post by sundar_ima on 2011-01-17
I recently bought 320 GB Trancend external hard disk and working fine until few days back. Earlier i could copy from and to the hard disk with out any issue. I dont know what happened after that now i am not able to write any files in to the external hard disk. This is not NTFS formatted device. here is some of the out put from terminal.

```
sundar@sundar-sundar:~$ fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xace2ace2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2550    20482843+   7  HPFS/NTFS
/dev/sda2   *        2551       14593    96735367    f  W95 Ext'd (LBA)
/dev/sda5            2551        5100    20482843+   b  W95 FAT32
/dev/sda6            5101        7650    20482843+   7  HPFS/NTFS
/dev/sda7            7651        9291    13178467+  83  Linux
/dev/sda8            9292        9361      562243+  82  Linux swap / Solaris
/dev/sda9            9362       10200     6739236   83  Linux
/dev/sda10          10201       11973    14241591    7  HPFS/NTFS
/dev/sda11          11974       14593    21045118+  83  Linux

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf354b7c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38913   312568641    c  W95 FAT32 (LBA)

```

Last few lines of dmesg 

```
sundar@sundar-sundar:~$ dmesg
.
.
.
[  541.827735] sd 7:0:0:0: Attached scsi generic sg1 type 0
[  541.828610] sd 7:0:0:0: [sdb] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[  541.831025] sd 7:0:0:0: [sdb] Write Protect is off
[  541.831037] sd 7:0:0:0: [sdb] Mode Sense: 34 00 00 00
[  541.831044] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  541.836717] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  541.836733]  sdb: sdb1
[  541.876890] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  541.876905] sd 7:0:0:0: [sdb] Attached SCSI disk

```

Content of /etc/fstab

```
sundar@sundar-sundar:~$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda10 during installation
UUID=6dd1c406-1f87-455a-9928-8240faf464a3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda11 during installation
UUID=21988580-3120-45e7-a790-ef93b87179c6 none            swap    sw              0       0

sundar@sundar-sundar:~$ 

```

content of /etc/mtab

```
sundar@sundar-sundar:~$ cat /etc/mtab 
/dev/sda11 / ext4 rw,errors=remount-ro,commit=0 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/sundar/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=sundar 0 0
/dev/sdb1 /media/Transcend vfat rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush 0 0
sundar@sundar-sundar:~$ 

```

and the ouutput of mount

```
sundar@sundar-sundar:~$ mount
/dev/sda11 on / type ext4 (rw,errors=remount-ro,commit=0)
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/sundar/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=sundar)
/dev/sdb1 on /media/Transcend type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
sundar@sundar-sundar:~$ 
```

Any help is appreciated...

---

### Post by sundar_ima on 2011-01-18
Any help???

---

### Post by Bitrate on 2011-01-18
Have you tried manually mounting the drive like this:

sudo mount -o umask=0 /dev/sdb1 /media/Transcend

---

### Post by sundar_ima on 2011-01-18
> **Bitrate said:**
> Have you tried manually mounting the drive like this:

sudo mount -o umask=0 /dev/sdb1 /media/Transcend

Thanks for the reply. Tried it now. But the result is same. Still i could not write anything in to the disk.

---

### Post by sundar_ima on 2011-01-18
I am surprised that when i tested my hard disk under windows it works fine. 

Any help?

---

### Post by deserthowler on 2011-01-18
Have you checked the permissions on the disk?

Earl

---

### Post by sundar_ima on 2011-01-20
Ok. Got it solved by accidental. This is what i did. Rebooted the Laptop with out knowing that my hard disk is attached to it. It booted from Windows and automatically moved into blue screen mode to check fault in the (external) hard disk. With out any intervention from me it was rectified by the windows. Now i dont have any issue with the external hard disk. In fact file transfer is faster that before.

Thank you all for your kind reply.

---

### Post by sundar_ima on 2011-01-20
Ok. Got it solved by accidental. This is what i did. Rebooted the Laptop with out knowing that my hard disk is attached to it. It booted from Windows and automatically moved into blue screen mode to check fault in the (external) hard disk. With out any intervention from me it was rectified by the windows. Now i dont have any issue with the external hard disk. In fact file transfer is faster that before.

Thank you all for your kind reply.

---

