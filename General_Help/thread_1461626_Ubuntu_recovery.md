---
title: "Ubuntu recovery"
date: 2010-04-24
forum: General Help
---

### Post by rdizzle1 on 2010-04-24
I have a IBM thinkpad t42 running ubuntu 9.1 which has recently crashed. On turning it back on it will say it is performing a disk check and will reach 26% before it never goes further. I am now running off a 9.1 live disk which just allows me basic internet functions. When trying to access the hard drive it comes up with an error stating "Process /lib/dbus-1.0/dbus-daemon-launch-helper received signal 7" I have no idea what this means. I just want to recover some critical work i had and reinstall but im stymied as to how to do this. Any suggestions would be much appreciated.

---

### Post by blueridgedog on 2010-04-24
Have you tried to mount the disk?

What is the output of the following commands?

```
sudo fdisk -l

```
and

```
mount
```

Do you have an external drive you can use to copy files to?  is it large enough to copy a rescue image of the failing drive to it?

---

### Post by rdizzle1 on 2010-04-24
I have a large enough backup drive, when i tell it to mount its spins up the cd then says nautilus has closed unexpectedly 

This is what it says when i sudo f disk:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4c57312b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9355    75144006   83  Linux
/dev/sda2            9356        9729     3004155    5  Extended
/dev/sda5            9356        9729     3004123+  82  Linux swap / Solaris

And then when i type Mount:

ubuntu@ubuntu:~$ mount
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /media/47926858-c18c-4459-b6c7-05e964156308 type ext3 (rw,nosuid,nodev,uhelper=devkit)
ubuntu@ubuntu:~$ ^C

I cant make heads or tails of it and it still wont let me open the drive without saying it encountered an error.

---

### Post by blueridgedog on 2010-04-24
Let's see if you can access it without Nautilus.

Can you open a terminal and take a look at the disk?  It appears to be mounted at /media/47926858-c18c-4459-b6c7-05e964156308, so I would:

```
cd /media/47926858-c18c-4459-b6c7-05e964156308
ls -al
```

From there you may be able to:

```
cd /media/47926858-c18c-4459-b6c7-05e964156308/home/USER
```

Change USER to your user account on the system.

and then copy your files to another location using the cp command.  The mount command and fdisk command did not show any external media that you could copy to, so I assume it was not plugged in at the time. 

If that fails, then I can help you make a rescue image of the failing drive.

---

### Post by rdizzle1 on 2010-04-24
This is what i get with that command:

ubuntu@ubuntu:~$ cd /media/47926858-c18c-4459-b6c7-05e964156308
ubuntu@ubuntu:/media/47926858-c18c-4459-b6c7-05e964156308$ ls -al
total 108
drwxr-xr-x  21 root root  4096 2010-03-10 18:39 .
drwxr-xr-x   3 root root    80 2010-04-24 18:10 ..
drwxr-xr-x   2 root root  4096 2010-01-31 18:12 bin
drwxr-xr-x   3 root root  4096 2010-03-18 19:47 boot
lrwxrwxrwx   1 root root    11 2009-11-17 20:35 cdrom -> media/cdrom
drwxr-xr-x   4 root root  4096 2009-04-20 14:06 dev
drwxr-xr-x 148 root root 12288 2010-04-09 01:38 etc
drwxr-xr-x   3 root root  4096 2009-11-17 20:52 home
lrwxrwxrwx   1 root root    33 2010-03-10 18:39 initrd.img -> boot/initrd.img-2.6.31-20-generic
lrwxrwxrwx   1 root root    33 2010-02-06 04:52 initrd.img.old -> boot/initrd.img-2.6.31-19-generic
drwxr-xr-x  18 root root 12288 2010-01-31 18:12 lib
drwx------   2 root root 16384 2009-11-17 20:35 lost+found
drwxr-xr-x   4 root root  4096 2010-04-06 15:38 media
drwxr-xr-x   2 root root  4096 2009-04-13 09:33 mnt
drwxr-xr-x   4 root root  4096 2009-12-29 04:51 opt
drwxr-xr-x   2 root root  4096 2009-04-13 09:33 proc
drwx------  13 root root  4096 2010-02-25 14:19 root
drwxr-xr-x   2 root root  4096 2010-03-26 08:48 sbin
drwxr-xr-x   2 root root  4096 2009-03-06 16:21 selinux
drwxr-xr-x   3 root root  4096 2009-12-29 04:51 srv
drwxr-xr-x   2 root root  4096 2009-03-31 09:02 sys
drwxrwxrwt  13 root root  4096 2010-04-09 01:38 tmp
drwxr-xr-x  12 root root  4096 2009-12-29 04:51 usr
drwxr-xr-x  15 root root  4096 2009-04-20 14:07 var
lrwxrwxrwx   1 root root    30 2010-03-10 18:39 vmlinuz -> boot/vmlinuz-2.6.31-20-generic
lrwxrwxrwx   1 root root    30 2010-02-06 04:52 vmlinuz.old -> boot/vmlinuz-2.6.31-19-generic

So now plugging in the portable drive what should i do to copy it over to that?

---

### Post by rdizzle1 on 2010-04-24
I now get this with the mount command with the portable plugged in:

ubuntu@ubuntu:~$ mount
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /media/47926858-c18c-4459-b6c7-05e964156308 type ext3 (rw,nosuid,nodev,uhelper=devkit)
/dev/sdb1 on /media/My Passport type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


 So whats the command i should type to copy over the old to the new? And when thats done how do i access it? Or will it just be like a directory full of openable files?

---

### Post by blueridgedog on 2010-04-24
I would open a terminal and copy your /home directory (assuming the files you want are there) to the external drive:

```
mkdir /media/My Passport/home
cp /media/47926858-c18c-4459-b6c7-05e964156308/home /media/My Passport/home
```

You may need quotes around the path given the space in the path name of "My Passport"

---

### Post by rdizzle1 on 2010-04-24
when i put in 
mkdir /media/My Passport/home

It says:

mkdir: cannot create directory `/media/My': Permission denied
mkdir: cannot create directory `Passport/home': No such file or directory
ubuntu@ubuntu:~$ cp /media/47926858-c18c-4459-b6c7-05e964156308/home /media/My Passport/home

---

### Post by JKyleOKC on 2010-04-25
As BlueRidgeDog indicated, you need quotes around the path:

```
sudo mkdir "media/My Passport/home"
```

That will also be necessary in the "cp" command. The bash shell uses the space character to separate arguments to commands, so the quotes are necessary to make it ignore the space in the directory name.

---

### Post by blueridgedog on 2010-04-25
I should have included them.  Try these:

```
mkdir "/media/My Passport/home"
cp /media/47926858-c18c-4459-b6c7-05e964156308/home "/media/My Passport/home"
```

---

### Post by rdizzle1 on 2010-04-25
Still says that it cant create 

ubuntu@ubuntu:~$ sudo mkdir "media/My Passport/home"
mkdir: cannot create directory `media/My Passport/home': No such file or directory

---

### Post by blueridgedog on 2010-04-25
Should be:

```
mkdir "/media/My Passport/home"
```

I left off the leading slash.

---

### Post by rdizzle1 on 2010-04-25
ubuntu@ubuntu:~$ cp /media/47926858-c18c-4459-b6c7-05e964156308/home "/media/My Passport/home"
cp: omitting directory `/media/47926858-c18c-4459-b6c7-05e964156308/home'

I think it allowed me to create the first directory but the cp command isnt working

---

### Post by blueridgedog on 2010-04-25
use:

```
cp /media/47926858-c18c-4459-b6c7-05e964156308/home/ -r "/media/My Passport/"
```

---

