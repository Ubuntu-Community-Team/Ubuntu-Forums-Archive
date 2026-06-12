---
title: "Can't mount Ntfs drives"
date: 2010-02-01
forum: General Help
---

### Post by stuart221 on 2010-02-01
ubuntu 9.10  when I try to mount internal drive
receive the following massage 
Error mounting: mount exited with exit code 1: helper failed with:
Remounting is not supported at present. You have to umount volume and then mount it once again.
were do I go from here?

---

### Post by Psumi on 2010-02-01
See if ntfs-3g is installed on your machine:

```
sudo apt-get install ntfs-3g
```

if it is, it will tell you that it is. Ubuntu should automount USB drives. Then again, I always use fat32 for my flash drives or any external drive, because my PS3 can't take anything else. ;)

---

### Post by stuart221 on 2010-02-01
used it did not work

---

### Post by slack on 2010-02-01
Are you certain it isn't already mounted?  What is the output of

```
mount
```

and

```
df
```

?

---

### Post by stuart221 on 2010-02-01
tuart@stuart-desktop:~$ mount
/dev/sdb1 on / type ext4 (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
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
gvfs-fuse-daemon on /home/stuart/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=stuart)
/dev/sr0 on /media/APCAPR08DVD type iso9660 (ro,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)
stuart@stuart-desktop:~$ 

Filesystem           1K-blocks Used Available Use% Mounted on
/dev/sdb1            234424824  16589540 205927108   8% /
udev                   1030284       312   1029972   1% /dev
none                   1030284       296   1029988   1% /dev/shm
none                   1030284       296   1029988   1% /var/run
none                   1030284         0   1030284   0% /var/lock
none                   1030284         0   1030284   0% /lib/init/rw
/dev/sr0               3083524   3083524         0 100% /media/APCAPR08DVD
stuart@stuart-desktop:~$

---

### Post by Psumi on 2010-02-01
-- Delete Post --

---

### Post by slack on 2010-02-01
and what's the exact command you're using to try and mount the drive?

---

### Post by stuart221 on 2010-02-02
command used is  sudo fdisk -l

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8900    71489218+   7  HPFS/NTFS
/dev/sda2            8901       60800   416886718+   7  HPFS/NTFS
/dev/sda3           60801       60801        8032+   f  W95 Ext'd (LBA)

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1d461d45

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       29650   238163593+  83  Linux
/dev/sdb2           29651       30401     6032407+   5  Extended
/dev/sdb5           29651       30401     6032376   82  Linux swap / Solaris
then use 

sudo umount /media/sda2
massage given
umount: /media/sda2: not found

---

### Post by rnerwein on 2010-02-02
hi
1. let us see the contens of /etc/fstab
2. if /dev/sda1 or /dev/sda2 is referenced then
3. sudo mount /dev/sda1 ( or /dev/sda2 ) should work 
4. if not: sudo mount /dev/sda1 /mnt ( /mnt should exists by default on your system)
ciao

---

### Post by stuart221 on 2010-02-02
UUID=829C2F399C2F26DF /media/windisk ntfs-3g remount,umask=007 1 0
UUID=01C8EE1778E52200 /media/sda2 ntfs-3g remount,group,dirsync,encryption,keyb$
UUID=9e56c06e-6756-40e2-a812-2b73ba49b056 / ext4 defaults 0 1
UUID=f428bf38-823d-4e02-a2d2-1d49f9f6883b swap swap sw 0 0

---

### Post by rnerwein on 2010-02-02
hi
oh looks like it's crypted - i'll give up - i never played with this stuff
sorry
ciao

---

### Post by mrkazoodle on 2010-02-02
Me neither, can you log in on your other OS and get rid of that encryption?

If you ever need to mount a drive: this tool will do it for you:

```
sudo apt-get install ntfs-config
```

(system>management>NTFS configuration tool)

---

