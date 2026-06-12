---
title: "File sharing problems"
date: 2009-12-03
forum: General Help
---

### Post by killa.fr0gg on 2009-12-03
Hi all!

I'm having a fabulous time using Ubuntu, but I am remiss to report that it is turning out to be completely incompatible with files created on other systems. For instance, before installing Ubuntu, I backed up my system. When I tried to move the backed up files into Ubuntu, it won't let me have access. WTF? I've done this countless times, just not with Ubuntu. The files open up fine on every other platform just fine without any permission problems. I can't even email so much as a document to myself, because if it comes from any other system it's all read-only and if I send something I created within the Ubuntu install it becomes read-only on all other systems. As you can imagine, this is playing merry hell with my productivity (and happiness! All of my work has been "lost" for all intents and purposes, but more importantly I HAVE NO MUSIC!!!!).

Please help save my sanity. This forum is always full of helpful advice and good answers, and I appreciate it very much.

Thank you

---

### Post by jbrown96 on 2009-12-03
It's a permissions issue. There are two ways to deal with this. You can allow "others" to have access to the files, or you can create a group on each system to allow access to the files. 

The "others" method is much easier, but could be slightly less secure if other users use the computer, but you don't want them to access the files. This probably isn't an issue. In a terminal (apps-->accessories) run ```
sudo chmod -R o+rw /path/to/files
```

For the second method, I would need to know the other systems that you are using, and you user ids on them.

---

### Post by killa.fr0gg on 2009-12-03
Hi, thank you for the reply. That command was not capable of letting me get access to the folders. When directed at one of the folders it returns

file_name : Read-only file system

However, it does solve my 'sharing with others' problem, so thank you very much. Unfortunately, the most pressing matter at hand is the lack of access to my back-up drive.

Thanks

---

### Post by jbrown96 on 2009-12-03
Could you mount your backup drive and post the output of the following commands. ```
sudo fdisk -l
``` ```
sudo lshw -class disk
``````
mount -l
``` ```
sudo ls -l /path/to/mount/location
``` that path is probably a folder in /media (usually /media/disk).

---

### Post by Rebelli0us on 2009-12-03
The only way to get full use of YOUR computer is to make friends with a guy named "root" and a dude called "sudo". The other way around the problem is to impersonate root, so whenever your comput0r asks you who you are, you just type "root".

---

### Post by killa.fr0gg on 2009-12-03
> **jbrown96 said:**
> Could you mount your backup drive and post the output of the following commands. ```
sudo fdisk -l
``` ```
sudo lshw -class disk
``````
mount -l
``` ```
sudo ls -l /path/to/mount/location
``` that path is probably a folder in /media (usually /media/disk).

sudo fdisk -l

```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           1         977   ef  EFI (FAT-12/16/32)
/dev/sda2   *           1       38173   306622070+  83  Linux
/dev/sda3           38173       38914     5948143   82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x31cbf397

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          26      204819+  ee  GPT
/dev/sdb2   *          26       30385   243862672   af  HFS / HFS+

```

```

sudo lshw -class disk
  *-cdrom                 
       description: DVD writer
       product: DVD-R   UJ-857E
       vendor: MATSHITA
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: ZB0E
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=open
  *-disk
       description: ATA Disk
       product: TOSHIBA MK3252GS
       vendor: Toshiba
       physical id: 0.1.0
       bus info: scsi@2:0.1.0
       logical name: /dev/sda
       version: LV01
       serial: 78T8P50AT
       size: 298GiB (320GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdb
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: signature=31cbf397

```

```
mount -l
/dev/sda2 on / type ext4 (rw,errors=remount-ro)
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdb2 on /media/The biz type hfsplus (rw,nosuid,nodev,uhelper=devkit) [The biz]

```

```
sudo ls -l /media/backup
drwx------ 1  99      99         45 2009-11-28 15:17 Documents
drwx------ 1 501 dialout         21 2009-11-28 20:18 Movies
drwx------ 1  99      99         75 2009-10-17 20:42 Music
drwxr-xr-x 1  99      99          6 2009-11-27 05:10 NetBeansProjects
drwx------ 1  99      99          7 2009-11-25 21:05 Pictures

```

Thank you

---

### Post by jbrown96 on 2009-12-03
You seem to be using hfs+; were these file system's created in Mac OS X? It's very possible that you need to install the hfs utilities to have write access to them. 

```
sudo apt-get install hfsplus hfsprogs hfsutils
``` un mount and then re-mount the drive. Then try the chmod command from my post earlier. I just tried creating an hfs+ partition (in Ubuntu), and I was able to chmod it fine. 

I'm confused about the contents of /media/The Biz. It's not listed as a mounted directory (mount -l), and neither is /media/backup. Have you created a link from /media/The Biz to /media/backup? What does ```
sudo ls -l /media/The Biz
``` return?

---

### Post by killa.fr0gg on 2009-12-03
> **jbrown96 said:**
> I'm confused about the contents of /media/The Biz. It's not listed as a mounted directory (mount -l), and neither is /media/backup. Have you created a link from /media/The Biz to /media/backup? What does ```
sudo ls -l /media/The Biz
``` return?

I'm sorry, in the interest of simplicity I just stated "/media/The biz" as "/media/backup"

What I have been able to do after some 'man'ing in the terminal was move all the files to my Desktop and from there use sudo chmod username file to give myself write access. I also have been able to use the terminal to fix my sharing issue. It is a workaround, to be sure, but it works. Is there a simpler way to do this?

---

### Post by jbrown96 on 2009-12-03
I think that if you install the three hfs utilities that I mentioned, then you should have write access to the drive, and then you won't need to move them to your desktop. You should be able to chmod them in place.

---

### Post by killa.fr0gg on 2009-12-04
@jbrown96: thank you for all of your assistance. Installing the hfs utilities seemed to do nothing at all.

---

### Post by jbrown96 on 2009-12-04
My guess is that Mac uses a form of hfs+ that Ubuntu doesn't understand, so Ubuntu mounts it read-only, so it doesn't mess it up.

HFS+ is a really unique file system. There really aren't any like it. It stores data and meta data completely separate places, which isn't normal. It's also not a very advanced file system, especially compared to Linux FSs. Maybe Apple made some tweaks (that Ubuntu doesn't understand) to improve hfs+ some. 

You could try to move everything off of there, and create a new hfs+ using ubuntu, and hopefully OS X can fully understand that. 

The other possibility would be to move everything off, then create a totally different file system that OS X and Ubuntu can use. There don't appear to be many good candidates: fat32 (vfat) and ntfs. It's funny to think that fat32 and ntfs (both Microsoft creations) are the best for compatibility!

---

### Post by killa.fr0gg on 2009-12-05
Hi.

Thanks for all of your help. Unfortunately, what ended up needing to happen was a lot of work at the command-line. I'm not complaining, though, it was kind of fun. For people with similar issues, in order to access the files I had to log in as root (sudo su) and use the command mv file_name /path/to/directory. After that, in order to give myself all the right priveleges, I had to change the ownersip of all the files with chown username /path/to/file. Friendly tip: use wild-cards as extensively as possible!

After that, I reformatted my external hard drive to FAT32, which has given me universal access to files placed on it again across all platforms. Looks like the simplest way around any and all permissions issues is still the command line. It would be nice if we could get some better support for file-sharing :)

If anyone else stumbles upon this thread and needs help with this issue, feel free to PM me for a more detailed synopsis of the steps I went through. And if yet another person stumbles upon this thread and knows of a better way around this, please share!

Thanks all, and special thanks to jbrown96!

---

