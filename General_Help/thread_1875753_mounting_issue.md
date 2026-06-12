---
title: "mounting issue"
date: 2011-11-05
forum: General Help
---

### Post by zoobie on 2011-11-05
Hi everyone,

Let me introduce myself i'm Zoobie and I'm French. Please note that I'm a noob in Linux and Ubuntu.

I need your help as I'm facing the following issue.

Please note that I have installed ubuntu 11.10 64 bits and I'm using webmin 1.570 as well to administer remotely my server.

I have two hd of 3tb that each of them I have splited in partitions of 1TB, and I have created 3 raid1 drive of 1TB and I have mounted them in the media folder please find below an extract of the fstab:


/dev/md127p1  /media/media3  ntfs  defaults  0  0
/dev/md125p1  /media/media1  ntfs  defaults  0  0
/dev/md126p1  /media/media2  ntfs  defaults  0  0

on the drive I have the following folder structure:

/media1/a/
/media2/b/
/media3/c/

when I'm trying to access the drive with the graphic interface in nautilus its working properly the /a folder is located on media1 but I try to access the drive through the console when I input the following command:

User$@NAS:/media/media1$ dir as the result i'm seeing the folder b/ which is located under nautilus on the media2 drive not on the media1 as seen trough the console. In the same way the folder /a is located on the drive media3 whereas in nautilus the folder is shown on drive media1.

Then my question is simple, how I can have the nautilus view and the console view aligned ?

Thanks for your answers

Regards,

Zoobie

---

### Post by dcstar on 2011-11-05
> **zoobie said:**
> Hi everyone,

Let me introduce myself i'm Zoobie and I'm French. Please note that I'm a noob in Linux and Ubuntu.

I need your help as I'm facing the following issue.

Please note that I have installed ubuntu 11.10 64 bits and I'm using webmin 1.570 as well to administer remotely my server.

I have two hd of 3tb that each of them I have splited in partitions of 1TB, and I have created 3 raid1 drive of 1TB and I have mounted them in the media folder please find below an extract of the fstab:


/dev/md127p1  /media/media3  ntfs  defaults  0  0
/dev/md125p1  /media/media1  ntfs  defaults  0  0
/dev/md126p1  /media/media2  ntfs  defaults  0  0

on the drive I have the following folder structure:

/media1/a/
/media2/b/
/media3/c/

when I'm trying to access the drive with the graphic interface in nautilus its working properly the /a folder is located on media1 but I try to access the drive through the console when I input the following command:

User$@NAS:/media/media1$ dir as the result i'm seeing the folder b/ which is located under nautilus on the media2 drive not on the media1 as seen trough the console. In the same way the folder /a is located on the drive media3 whereas in nautilus the folder is shown on drive media1.

Then my question is simple, how I can have the nautilus view and the console view aligned ?

Thanks for your answers

Regards,

Zoobie

[LIST=1]
[*]Do **not** use /media for any fstab use, /media is a system folder that things like the Gnome desktop use for mounting things - use /mnt for mounting.
[*]Your drives are not being mounted correctly, use ```
mount
``` to see what is actually being done.
[/LIST]

---

### Post by zoobie on 2011-11-07
Hi David,

Thanks for your feedback, I have changed the parameter in fstab in order to mount the raid1 drives under mnt.

I have also use the mount command, please find below the result:

/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
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
/dev/sda3 on /tmp type ext4 (rw,commit=0)
/dev/md125p1 on /mnt/xbmc/media3 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/md127p1 on /mnt/xbmc/media1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/md126p1 on /mnt/xbmc/media2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb4 on /media/donnee type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda8 on /media/admin type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda4 on /home type ext4 (rw,commit=0)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/deneufchatel_family/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=deneufchatel_family)

the funny think is that for example the md127p1 is changing after every reboot sometime it's point me on folder a, sometime b sometime c. it seems that this md12Xp1 devices are variable and not static value. Do you know how I can fix them to be static and not variable.

Thanks and regards,

Zoobie

---

### Post by scottbomb on 2011-11-08
Here's where I learned to fstab:

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

I mount my drives in fstab by UUID. It's the most reliable way to go because sometimes the kernel changes the /dev/sda# on bootup. Not sure why, I think it has something to do with the way BIOS reports the drives on startup. In fact, in your fstab file, you'll likely see the boot drive referred to by UUID for this very reason - it's more reliable.

---

