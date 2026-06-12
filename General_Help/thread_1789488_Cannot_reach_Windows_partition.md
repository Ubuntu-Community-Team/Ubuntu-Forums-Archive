---
title: "Cannot reach Windows partition"
date: 2011-06-23
forum: General Help
---

### Post by yc2 on 2011-06-23
Hi,

I run 11.04 from a USB-stick according to instructions on ubuntu.com (pendrivelinux) with persistence. I use an Acer Aspire One D255E (10" screen notebook).

I cannot reach the Windows partition. (Win7 starter. It is not hibernated.) It was OK at first but the error then occurred suddenly. It has happened before and the only thing that helps is reinstallation. The problem causes me much trouble. I must find a way to reach the files. (There is no problem reaching the 4.3 G android partition. I always unmount Win before shutting down, but that does not seem to be the issue. When I tried to investigate the problem earlier I intentionally left Win mounted at shutdown, but it could not provoke the issue.)

I am advised to use the fuser command, I do not know how. Here are some data:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x90720c37

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1698    13631488   27  Unknown
/dev/sda2            1698        2220     4194304    c  W95 FAT32 (LBA)
/dev/sda3   *        2220        2233      102400    7  HPFS/NTFS
/dev/sda4            2233       60802   470456320    f  W95 Ext'd (LBA)
/dev/sda5            2233       60802   470455296    7  HPFS/NTFS

Disk /dev/sdb: 8011 MB, 8011120640 bytes
16 heads, 32 sectors/track, 30560 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd9b9bb61

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30560     7823344    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ sudo umount /dev/sda5
umount: /dev/sda5: not mounted
ubuntu@ubuntu:~$ cd De*
ubuntu@ubuntu:~/Desktop$ mkdir acermp
ubuntu@ubuntu:~/Desktop$ sudo mount -B -t ntfs /dev/sda5 acermp
mount: Not a directory
ubuntu@ubuntu:~/Desktop$ ls /media
cdrom
ubuntu@ubuntu:~/Desktop$ 

```

Thanks, I would be really happy to solve this.

Screenshot enclosed.

---

### Post by ruffEdgz on 2011-06-23
To run the 'fuser' command, you do it this way:
```

sudo fuser -a /dev/sda*

```
This will check all the sda drives but I don't know how useful it will be without knowing the mount point(s) for /dev/sda5.

Was more curious about the mounting part. Run the command below and show the result on your next post:
```

mount

```
As a side note, the reason why your mount didn't work was because it didn't know the mount point was a directory. Try this the below command for mounting /dev/sda5 to your Desktop:
```

sudo mount -B -t ntfs /dev/sda5 ~/Desktop/acermp/

```
Hope this can help.

---

### Post by yc2 on 2011-06-23
Thanks a lot, I very much want to solve this. Here are additional data. (Sorry for not giving output of "mount" in the first post, I was clumsy w. the editing.)

```
ubuntu@ubuntu:~$ sudo fuser -a /dev/sda*
Cannot stat file /proc/4045/fd/21: Stale NFS file handle
Cannot stat file /proc/4045/fd/22: Stale NFS file handle
Cannot stat file /proc/4543/fd/67: Stale NFS file handle
Cannot stat file /proc/4543/fd/79: Stale NFS file handle
Cannot stat file /proc/4543/fd/80: Stale NFS file handle
Cannot stat file /proc/4543/fd/81: Stale NFS file handle
Cannot stat file /proc/4543/fd/83: Stale NFS file handle
Cannot stat file /proc/4543/fd/84: Stale NFS file handle
Cannot stat file /proc/4543/fd/85: Stale NFS file handle
Cannot stat file /proc/4543/fd/95: Stale NFS file handle
/dev/sda:
/dev/sda1:
/dev/sda2:
/dev/sda3:
/dev/sda4:
/dev/sda5:
ubuntu@ubuntu:~$ mount
rootfs on / type rootfs (rw)
none on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
none on /proc type proc (rw,nosuid,nodev,noexec,relatime)
none on /dev type devtmpfs (rw,relatime,size=1017956k,nr_inodes=214711,mode=755)
none on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
/dev/sdb1 on /cdrom type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
/dev/loop1 on /cow type ext2 (rw,noatime,errors=continue)
aufs on / type aufs (rw,noatime,si=748c7b08)
none on /sys/kernel/debug type debugfs (rw,relatime)
none on /sys/kernel/security type securityfs (rw,relatime)
none on /dev/shm type tmpfs (rw,nosuid,nodev,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
none on /var/run type tmpfs (rw,nosuid,relatime,mode=755)
none on /var/lock type tmpfs (rw,nosuid,nodev,noexec,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,nosuid,nodev,noexec,relatime)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,relatime,user_id=999,group_id=999)
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ cd De*
ubuntu@ubuntu:~/Desktop$ mkdir acermp
ubuntu@ubuntu:~/Desktop$ sudo mount -B -t ntfs /dev/sda5 ~/Desktop/acermp/
mount: Not a directory
ubuntu@ubuntu:~/Desktop$ 

```

---

### Post by ruffEdgz on 2011-06-24
Thanks for the output of the commands you did.

The 'mount' output is what I thought but wanted to make sure.

As for the mount command, it was my fault in not making sure what -B did which we don't need in this case. The '-B' option helps you bind and old directory to a new directory without unmounting the partition in the process. Try using the command below to mount the partition /dev/sda5 to your desktop:
```

sudo mount.ntfs /dev/sda5 ~/Desktop/acermp/

```
Lets just see if this gets the partition to mount.

If it does work, we can make this mounting process happen every time your Ubuntu instance starts (using your fstab file). If you can post back the results of these commands, that would be very helpful:
```

sudo blkid /dev/sda5

```
and
```

cat /etc/fstab

```

---

### Post by yc2 on 2011-06-24
Thanks a lot. Sorry for delay in my response, I am on a trip. I supply data below. I still can't get the bleeding partition mounted correctly ;)

```
ubuntu@ubuntu:~$ cd De*
ubuntu@ubuntu:~/Desktop$ mkdir acermp
ubuntu@ubuntu:~/Desktop$ sudo mount.ntfs /dev/sda5 ~/Desktop/acermp/
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
ubuntu@ubuntu:~/Desktop$ sudo blkid /dev/sda5
/dev/sda5: LABEL="Acer" UUID="DE0E512C0E50FEC9" TYPE="ntfs" 
ubuntu@ubuntu:~/Desktop$ cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
ubuntu@ubuntu:~/Desktop$ 

```

---

### Post by yc2 on 2011-06-27
** BUMP **
I would really appreciate some input on this.

It seems to me that I have been left with a "**[COLOR="Red"]stale NFS handle[/COLOR]**" to the ntfs partition.

The standard way to solve this seems to be unmount, but it does not work:
```
ubuntu@ubuntu:~/Desktop$ sudo umount -f /dev/sda5
umount2: Invalid argument
umount: /dev/sda5: not mounted

```
Probably because sda5 is not mounted any longer, maybe it is busy in some other way?? Some other program using it or some flag not reset. Or never unmounted properly?

If I knew the original mountpoint to the Windowspartition I would maybe be helped, but I do not know its name. (I guess it once resided in /media or /etc/mtab?)

```
ubuntu@ubuntu:~/Desktop$ cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
ubuntu@ubuntu:~/Desktop$ 
ubuntu@ubuntu:~/Desktop$ cat /etc/mtab
cat: /etc/mtab: No such file or directory
ubuntu@ubuntu:~/Desktop$ 
ubuntu@ubuntu:~/Desktop$ ls /media
cdrom

```

(Dolphin gets the same error as Nautilus. ntfs-config will not open at all)

Thanks.


[COLOR="Silver"]EDIT: "find" will find mtab, but cat will not.
```
ubuntu@ubuntu:~$ find / -name 'mtab' 2>/dev/null
/etc/mtab
/var/lib/udisks/mtab
ubuntu@ubuntu:~$ cat /etc/mtab
cat: /etc/mtab: No such file or directory
ubuntu@ubuntu:~$ sudo cat /etc/mtab
cat: /etc/mtab: No such file or directory
ubuntu@ubuntu:~$ ls /etc/mtab
/etc/mtab
ubuntu@ubuntu:~$ ls /etc/mtab/*
ls: cannot access /etc/mtab/*: No such file or directory
ubuntu@ubuntu:~$ cat /var/lib/udisks/mtab
ubuntu@ubuntu:~$ 

```[/COLOR]

EDIT:
Another try (instructions on Pendrivelinux homepage):
```

ubuntu@ubuntu:/$ sudo mkdir /media/windows
ubuntu@ubuntu:/$ sudo mount /dev/sda5 /media/windows/ -t ntfs -o nls=utf8,umask=0222
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
ubuntu@ubuntu:/$ ls /media/windows
ubuntu@ubuntu:/$ 

```

---

