---
title: "USB permissions issues"
date: 2011-08-24
forum: General Help
---

### Post by shadowofgrael on 2011-08-24
I have been trying to install Katana onto an 8GB flash drive and have had nothing but permission issues since starting. Katana is an expansive multi-purpose toolkit meant to be booted off of a flash drive.

I have expanded the rar file into the root directory of the flash drive which is formated as FAT32 as is required. As I understand it, permissions on FAT are either radically different or non-existent. What I do not understand is why some files are executable while others are not regardless of how hard I try to modify permissions of files on the device.

To set up the device as a bootable one is supposed to run a script called bootinst.sh or bootinst.bat depending on platform. I have been unable to start this script due to it being read only.

```
root@will-Latitude-E6400:/media/Katana# mount
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/will/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=will)
/dev/sr0 on /media/CSDevelopmentEnv type udf (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077,dmode=0500)
/dev/sdc1 on /media/Katana type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
root@will-Latitude-E6400:/media/Katana# ls -l
total 96
-rw-r--r--   1 will will   162 2010-10-22 21:23 autorun.inf
drwx------   4 will will  4096 2011-08-24 20:14 backtrack
drwx------   8 will will  4096 2011-08-24 20:44 boot
drwx------  10 will will  4096 2011-08-24 20:16 caine
drwx------   2 will will  4096 2011-08-24 20:17 dban
drwx------   3 will will  4096 2011-08-24 20:17 docs
drwx------   5 will will  4096 2011-08-24 20:17 Documents
drwx------   3 will will  4096 2011-08-24 20:17 forge
-rw-r--r--   1 will will  2943 2010-10-22 21:27 index.html
-rw-r--r--   1 will will     0 2010-10-22 21:27 katana
-rwxr-xr-x   1 will will 26624 2010-10-22 21:27 KatanaToolKit.exe
-rw-r--r--   1 will will  1217 2010-10-22 21:27 license.txt
drwx------   2 will will  4096 2011-08-24 20:17 live
drwx------ 100 will will  8192 2011-08-24 20:38 PortableApps
drwx------   2 will will  4096 2011-08-24 20:39 puppy
drwx------   4 will will  4096 2011-08-24 20:41 tables
drwx------   3 will will  4096 2011-08-24 20:42 trk3
drwx------   7 will will  4096 2011-08-24 20:42 ubcd
root@will-Latitude-E6400:/media/Katana# cd boot
root@will-Latitude-E6400:/media/Katana/boot# ls -l
total 316
-rwxr-xr-x 1 will will   2410 2011-08-24 20:44 bootinst.bat
-rw-r--r-- 1 will will   2410 2010-10-22 21:26 bootinst.sh
-rw-r--r-- 1 will will  12372 2010-10-22 21:26 chain.c32
-rw-r--r-- 1 will will   5384 2010-10-22 21:26 econfig.c32
drwx------ 3 will will   4096 2011-08-24 20:14 isolinux
-rwxr-xr-x 1 will will    712 2010-10-22 21:26 make_iso.bat
-rw-r--r-- 1 will will    962 2010-10-22 21:26 make_iso.sh
-rw-r--r-- 1 will will  29892 2010-10-22 21:26 menu.c32
drwx------ 2 will will   4096 2011-08-24 20:14 menus
drwx------ 3 will will   4096 2011-08-24 20:14 pxelinux.cfg
-rw-r--r-- 1 will will    776 2010-10-22 21:26 reboot.c32
drwx------ 7 will will   4096 2011-08-24 20:14 syslinux
drwx------ 2 will will   4096 2011-08-24 20:14 ubcd4win
drwx------ 2 will will   4096 2011-08-24 20:14 uninstall
-rw-r--r-- 1 will will 140580 2010-10-22 21:26 vesamenu.c32
-rw-r--r-- 1 will will  11174 2010-10-22 21:26 wallpaper_high.png
-rw-r--r-- 1 will will  62996 2010-10-22 21:26 wallpaper.png
root@will-Latitude-E6400:/media/Katana/boot# chmod +x bootinst.sh
root@will-Latitude-E6400:/media/Katana/boot# ls -l
total 316
-rwxr-xr-x 1 will will   2410 2011-08-24 20:44 bootinst.bat
-rw-r--r-- 1 will will   2410 2010-10-22 21:26 bootinst.sh
-rw-r--r-- 1 will will  12372 2010-10-22 21:26 chain.c32
-rw-r--r-- 1 will will   5384 2010-10-22 21:26 econfig.c32
drwx------ 3 will will   4096 2011-08-24 20:14 isolinux
-rwxr-xr-x 1 will will    712 2010-10-22 21:26 make_iso.bat
-rw-r--r-- 1 will will    962 2010-10-22 21:26 make_iso.sh
-rw-r--r-- 1 will will  29892 2010-10-22 21:26 menu.c32
drwx------ 2 will will   4096 2011-08-24 20:14 menus
drwx------ 3 will will   4096 2011-08-24 20:14 pxelinux.cfg
-rw-r--r-- 1 will will    776 2010-10-22 21:26 reboot.c32
drwx------ 7 will will   4096 2011-08-24 20:14 syslinux
drwx------ 2 will will   4096 2011-08-24 20:14 ubcd4win
drwx------ 2 will will   4096 2011-08-24 20:14 uninstall
-rw-r--r-- 1 will will 140580 2010-10-22 21:26 vesamenu.c32
-rw-r--r-- 1 will will  11174 2010-10-22 21:26 wallpaper_high.png
-rw-r--r-- 1 will will  62996 2010-10-22 21:26 wallpaper.png
root@will-Latitude-E6400:/media/Katana/boot# 

```

I have been able to work around the .sh error by copying it to the .bat and running the .bat from the device root directory. This, however, only ends in more permissions errors encountered by the script.

For what it is worth, here is what fdisk reports about the device 
```
root@will-Latitude-E6400:~/KATANA/boot# fdisk /dev/sdc1

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

Command (m for help): p

Disk /dev/sdc1: 8103 MB, 8103363072 bytes
250 heads, 62 sectors/track, 1021 cylinders
Units = cylinders of 15500 * 512 = 7936000 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

     Device Boot      Start         End      Blocks   Id  System
/dev/sdc1p1               1        1021     7911726    b  W95 FAT32

Command (m for help): 

```

---

### Post by TeoBigusGeekus on 2011-08-25
Fat and ntfs have no way of understanding linux permissions (or any permissions whatsoever).
Copy the files on a linux partition, change their permissions and then move them to the flash drive again.

---

### Post by seawolf167 on 2011-08-25
> **shadowofgrael said:**
> 
To set up the device as a bootable one is supposed to run a script called bootinst.sh or bootinst.bat depending on platform. I have been unable to start this script due to it being read only.

So I looked up the instructions and found [this]("http://www.hackfromacave.com/katana.html#katana_installation"). The only possibly solution that I can see if he did actually mean FAT32 would be to mount your flash drive with exec and rw as options which will make everything executable and allow read/writing then run the script.

So maybe

```
mount /media/flash_drive_mount_point -remount,exec,rw
```then run the script

```
cd /media/flash_drive_mount_point/boot
./bootinst.sh
```If that doesn't work, then you'll have to format the drive in a linux format as TeoBigusGeekus said since it allows for permissions to be stored.

---

### Post by shadowofgrael on 2011-08-29
Seawolf's solution is exactly what I was looking for, a way to mount the device with necessary permissions.

---

### Post by seawolf167 on 2011-08-29
Is everything installed and working as it is supposed to now?

---

