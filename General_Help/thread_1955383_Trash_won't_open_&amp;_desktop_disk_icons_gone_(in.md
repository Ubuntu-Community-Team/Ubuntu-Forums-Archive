---
title: "Trash won't open &amp; desktop disk icons gone (incl. USB)"
date: 2012-04-09
forum: General Help
---

### Post by sciemulo on 2012-04-09
I run an Acer Aspire 5742G-7308 with a Windows 7 / Xubuntu 11.10 (Oneiric) dual boot.

I  turned on my computer today to find that my desktop disk icons except  for Filesystem are gone. I previously had two icons for the Windows  Recovery partition and the main Windows partition with all my data. All  mounting was automatic upon clicking and at default settings.

I plugged  in my external USB Hard drive and none of its partitions show on the  desktop either. The same with the DVD drive. This previously worked just fine.

I was also confused to find that my trash bin's icon on the auto-hidden tray on the bottom  of the screen shows a "do-not-enter" symbol, and merely states "Failed  to connect to the Trash. Operation not supported."

My roommate uses Windows on this computer. He doesn't know the linux password, so when he logs on, he just reboots it in windows, and thats it. The worst I could imagine him doing is turning it off with the power button, but he claims he didn't do anything.

-I first checked that windows still ran properly; it does.

-I  then attempted to mount my windows drive manually in linux; it said  there were minor errors on the drive (possibly due to an improper windows shutdown), it fixed them automatically, it mounted normally  and works fine, but the icons still won't appear on the desktop.

-I ran fsck by:
```
sudo touch /forcefsck
```and restarted so it would check for errors. It did, and presumably fixed whatever it found (if anything). No effect.

-I manually emptied the trash bins of both my user and root using:
```
sudo thunar
```and  navigating to /home/(username)/.local/share/Trash/files/ ,  /home/(username)/.local/share/Trash/info/ ,  /root/.local/share/Trash/files/ , and /root/.local/share/Trash/info/ and  SHIFT-DEL'ing the contents. No effect after reboot.
---
```
cat /etc/fstab
```produces (some comments and white space edited out for this)
```
proc /proc proc nodev,noexec,nosuid 0 0
#this UUID is /dev/sda5
UUID=020f1a96-645b-4048-89e6-0bf3ad89ad3e / ext4 errors=remount-ro 0 1
/dev/mapper/cryptswap1 none swap sw 0 0
```---
```
sudo fdisk -l /dev/sda
```(main internal disk) produces
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x91073fcc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    29362175    14680064   27  Hidden NTFS WinRE
/dev/sda2   *    29362176    29566975      102400    7  HPFS/NTFS/exFAT
/dev/sda3        29566976   402982911   186707968    7  HPFS/NTFS/exFAT
/dev/sda4       402984958   976771071   286893057    5  Extended
/dev/sda5       402984960   968665087   282840064   83  Linux
/dev/sda6       968667136   976771071     4051968   82  Linux swap / Solaris
```---
```
sudo fdisk -l /dev/sdb
```(external usb hard drive) produces
```
Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8fbb2bd0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048     2099199     1048576    6  FAT16
/dev/sdb2         2099200   614651903   306276352    7  HPFS/NTFS/exFAT
/dev/sdb3   *   614651904   625137663     5242880    c  W95 FAT32 (LBA)
```---
```
mount
```produces
```
/dev/sda5 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/home/ulo/.Private  on /home/ulo type ecryptfs  (ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=(code),ecryptfs_fnek_sig=(code)
```---
Not really sure where to go from here. Any suggestions for how I can get my disk icons back on my desktop, and my trash bin functional again?

---

### Post by sciemulo on 2012-04-09
Update:

Ran Knoppix LiveDVD to try fsck

```
fsck.ext2 /dev/sda5
```produced
```
e2fsck 1.41.12 (17-May-2010)
Superblock last mount time is in the future.
    (by less than a day, probably due to the hardware clock being incorrectly set)  Fix<y>? yes

Superblock last write time is in the future.
    (by less than a day, probably due to the hardware clock being incorrectly set).  Fix<y>? yes

/dev/sda5: clean, 287184/17678336 files, 5687500/70710016 blocks (check after next mount)
```Will reboot and post again as to whether it did anything.

---

### Post by sciemulo on 2012-04-09
Still no effect.

---

### Post by sciemulo on 2012-04-09
Bump.

---

### Post by Peripheral Visionary on 2012-04-10
I'm not sure I understand all that terminal gobbldygook, but to change the settings so that desktop icons are visible:

Right-click anywhere on the desktop, choose **Applications > Settings > Xfce4 Settings Manager > Desktop** and click on the **Icons** tab. Make sure the ones you want on your desktop are checked, and uncheck the ones you don't want. **Removable Devices** is among the icons you can have appear on your desktop whenever a CD or USB device is inserted.

---

