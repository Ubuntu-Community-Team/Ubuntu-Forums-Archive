---
title: "Can't change group even though I own directory!"
date: 2010-10-12
forum: General Help
---

### Post by josephellengar on 2010-10-12
Hello!  I am trying to change the group of a directory in my home directory.  I recently changed my home directory to a separate partition, and it seems that it screwed things up, and made everything part of the "root" group and owned by "root."  I was able to change everything back to owned by me, except for the directory "flash," which is where I mount my flash drive.  I own the directory, but it is part of the root group.  When the flash drive is not mounted, the directory is owned by me and part of my group.  I can't figure it out.  Here is some terminal output:

```

ross@ross-laptop:~$ ls -l
total 28
drwx------ 2 ross ross   4096 Oct 11 19:51 Desktop
drwxrwxrwx 8 ross root   4096 Dec 31  1969 flash
drwx------ 4 ross ross   4096 Oct 12 19:49 gpodder-downloads
drwxr-x--- 1 ross users 16384 Oct 12 20:06 storage
ross@ross-laptop:~$ sudo chgrp ross flash
chgrp: changing group of `flash': Operation not permitted

```

And here is my fstab (if it matters):
```

 /etc/fstab: static file system information.
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0

# root filesystem
UUID=098c0e33-2ea8-420a-a7c9-2bcdc9011118 / ext4 errors=remount-ro,discard 0 1

# swap file
UUID=0de4ba0c-7406-4974-a25b-a1d10f68be39 none swap sw 0 0

#home
/dev/sda6 /home ext4 errors=remount-ro,discard 0 1

#storage
/dev/sdb1 /home/ross/storage ntfs-3g auto,exec,user,uid=1000,gid=100,dmask=027,fmask=137,utf8 0 0

#flash drive
/dev/sdc1 /home/ross/flash vfat iocharset=utf8,umask=000,user,noauto,exec 0 0



#tmpfs
tmpfs /tmp tmpfs defaults,noatime 0 0
tmpfs /var/tmp tmpfs defaults,noatime 0 0
tmpfs /var/log tmpfs defaults,noatime 0 0
tmpfs /var/log/apt tmpfs defaults,noatime 0 0

```

I'm stumped.  Any ideas?

---

### Post by josephellengar on 2010-10-13
bump

---

### Post by endotherm on 2010-10-13
try chown
```
sudo chown ross:ross ~/flash
```

---

### Post by josephellengar on 2010-10-13
> **endotherm said:**
> try chown
```
sudo chown ross:ross ~/flash
```

:(

```

ross@ross-laptop:~$ sudo chown ross:ross ~/flash
chown: changing ownership of `/home/ross/flash': Operation not permitted

```

---

### Post by coffeecat on 2010-10-13
> **rossholley said:**
> :(

```

ross@ross-laptop:~$ sudo chown ross:ross ~/flash
chown: changing ownership of `/home/ross/flash': Operation not permitted

```

Was sdc1 mounted to ~/flash when you tried the sudo chown? Doing a sudo chown on a mountpoint where a partition is mounted to it has the effect of chown-ing the root of the mounted filesystem, not the mountpoint. This is very useful with a Linux filesystem but since you can't chown a FAT32 filesystem and sdc1 is FAT32, I wonder if this is the problem.

Try unmounting sdc1 from ~flash and then retrying the sudo chown.

---

### Post by sisco311 on 2010-10-13
Check out: [thread=283131]How to fstab[/thread].

FAT & NTFS do not support Linux ownership and file permissions. You have to set the ownership and permissions at mount time with the uid,gid,umask,dmask and fmask mount options.

Also device names (/dev/sdXY) may change between system boots, you should use UUIDs. [uhelp]community/UsingUUID[/uhelp]

For the home partition use the **relatime** mount option. The  sixth field in fstab, (fs_passno), is used by the [noparse]fsck(8)[/noparse] program to determine the order in which filesystem checks are done at reboot time.  The root  filesystem  should  be specified with a fs_passno of 1, and other filesystems should have a fs_passno of 2.
```
UUID=uuid-of-the-partition   /home    ext4    relatime    0    2
```

---

