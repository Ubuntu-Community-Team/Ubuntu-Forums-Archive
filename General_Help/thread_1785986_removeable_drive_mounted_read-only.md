---
title: "removeable drive mounted read-only"
date: 2011-06-19
forum: General Help
---

### Post by evilbrent on 2011-06-19
I have a portable hard drive that says its a read-only filesystem, although I have read-write access to all the files ok.

I've found that I could do

```
Unmount the device.
mount -o rw /device /mountpoint. 
```

but what to put for /device and /mountpoint?

I think it's at /media/sdb1

---

### Post by kuifje09 on 2011-06-19
When you start tail -f on the kern.log you can see the drive beeing plugged in.

tail -f /var/log/kern.log

Plug in the drive.
Then the drive will be mounted ( readonly ? )
You can umount it  and remount it on any directory you like. 
Best not to let it overlap any directory as you will understand.

The drive is mounted read-only? Then there might be a problem.

After unount </dev/sdXX>  check it whithout writing first with

fsck -n </dev/sdXX>

( I have had troubles in writing to NTFS in the past, so I mount those only read-Only , and never check them on linux )

Options to fsck depend partialy on the type of filesystem.

If you know what the problem is, take further steps to resolve...

---

### Post by evilbrent on 2011-06-19
uh, ok. I did those commands but the outputs didn't mean anything to me.

do I write /dev/sdb1 for the /mountpoint and /media/sdb1 for the /device??

---

### Post by evilbrent on 2011-06-19
I went ahead and tried

```
sudo mount -o rw /dev/sdb1 /media/sdb1
```

and it's still saying that it's a read-only filesystem.

How can I change this to a read-write filesystem?

---

### Post by kuifje09 on 2011-06-19
Okay, this means there is a little problem.

Try   "sudo fsck -n /dev/sdb1 "    and show what it said.

Can you also do   " ls -ld /media/sdb1  " when the disk is mounted and show the output

---

### Post by evilbrent on 2011-06-19
Hi, thanks heaps for getting back to me!

```
brent@Bertha:~$ sudo fsck -n /dev/sdb1
[sudo] password for brent: 
fsck from util-linux-ng 2.17.2
dosfsck 3.0.7, 24 Dec 2009, FAT32, LFN
open: No such file or directory
```

but if I run mount I get
```

brent@Bertha:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro,user_xattr)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /var/lib/ureadahead/debugfs type debugfs (rw,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/brent/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=brent)
/dev/sda2 on /media/867CF7DF7CF7C847 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1 on /media/sdb1 type vfat (rw,noexec,nosuid,nodev,user=brent)
/dev/sdc1 on /media/x type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)

```

 - but it doesn't seem to be able to work out if x is /media/x or /media/sdb1. I think I might have mounted it as /media/x at some point. Either way it looks rw to me. I reran the fsck with /media/x just in case it means something:

```
brent@Bertha:~$ sudo fsck -n /media/x
[sudo] password for brent: 
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /media/x
Could this be a zero-length partition?
```

You also asked to see 
```

brent@Bertha:~$ ls -ld /media/sdb1
drwxr-xr-x 10 brent root 16384 1970-01-01 10:00 /media/sdb1
```

I think this says that the files in the drive are writeable for the owner brent - that's me - which is what nautlius says.

The files are read-write, but the filesystem itself is acting read-only.


I looked at /etc/fstab and it contains

```
proc                                       /proc        proc  nodev,noexec,nosuid           0  0  
UUID=cc7b51e8-18e0-4d07-9268-c5538a2abf73  none         swap  sw                            0  0  
UUID=d4278f40-2c1b-4cb5-82ef-0948deec2af5  /            ext4  errors=remount-ro,user_xattr  0  1  
/dev/sdb1                                  /media/sdb1  vfat  users,user                    0  0  
```

Which I think doesn't mention the filesystem. Should I try to edit that last line to put a rw in there somewhere??

---

### Post by evilbrent on 2011-06-20
i changed my fstab to something else and then back again and now it says that /sdb1 doesn't exist when I mount it.

---

### Post by kuifje09 on 2011-06-20
Okay to be more presice, I did not ask for fsck -n /media/<>  but for  fsck -n /dev/sdb1.

This way you try to check a directory, which is not intended.

Sorry, forgot this.
First plug in your drive, then umount it by hand. This wiil keep your devicefile alive.
Automatic umount can delete the devicefile.
When you do a tail -f /var/log/kern.log, you will see the drive come active, with its devicefile and number

fsck is done on a _unmounted_ device.   else mount will complain and in some cases it will destroy your file system, so it will prevent you from doeing that in the first place.

So /dev,whatever> is a device   and /media/<whatever>  are default mountpoints for automatic mounts.

I see in your output it is about a vfat filesystem, so could it be checked.

But first   fsck -n /dev/sdb1    and depending on  what you get,   fsck -y /dev/sdb1

Also... You say /media/x   , thats about drive /dev/sdc1   , be  aware what you do...

If you realy talk about a usb drive, its not needed to have it in your fstab.
And yes,  your fstab can cause trouble when you try to mount the same /dev/... by hand.

( Also i see both  sdb1  an sdc1 are mouted "rw" )  So you fixed it already ?

---

