---
title: "Auto mount drive help"
date: 2009-06-29
forum: General Help
---

### Post by megavolt1 on 2009-06-29
I am running Ubuntu 9.04 amd64 and I can't seem to mount my hard drives on login. From what I have read, I think it is a fstab config issue but I am not sure how to configure ubuntu to auto mount the drives.

There are 3 500Gb SATA2 drives formated to NTFS

Can someone please let me know if I am on the right track, and/or how to configure the system to automount the drives.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=97efa421-875b-4ee8-96c8-c1f53bceb769 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=337deb12-1e65-4c1b-a032-50098bf65ba0 /home           ext3    relatime        0       2
# /dev/sda3
UUID=32ddc3a6-9a18-4f0b-9672-8e9a756af7b0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by t4thfavor on 2009-06-29
add an entry that looks something like this to /etc/fstab

replace the uuid with your disks uuid, and the ext4 with ntfs-3g, also change the mount point to something like /media/disk-x where x is the disk number.


# /dev/sdb1 for ftp
UUID=6c466b41-1e02-4c45-b76e-c60f7bef1b8a /home/FTP-shared               ext4    relatime,errors=remount-ro 0       1

Find the uuid by this command

ls -lah /dev/disk/by-uuid



My complete /etc/fstab where the one marked FTP was added there by me, and mounts everytime I boot.


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=adf3927b-aa18-4cb8-ac9b-8fae733d0746 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=42d7e60e-62b5-4c9d-b282-83ebfb3e4bc9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/sdb1 for ftp
UUID=6c466b41-1e02-4c45-b76e-c60f7bef1b8a /home/FTP-shared               ext4    relatime,errors=remount-ro 0       1

---

### Post by merlinus on 2009-06-29
An easier way might be this.

```

sudo apt-get install ntfs-config

```Restart, and ntfs config should appear in the Applications/System Tools menu, or possibly somewhere else there.  Tick the appropriate boxes, restart again, and IIRC they should automount without having to edit /etc/fstab.

---

### Post by DeMus on 2009-06-29
> **merlinus said:**
> An easier way might be this.

```

sudo apt-get install ntfs-config

```Restart, and ntfs config should appear in the Applications/System Tools menu, or possibly somewhere else there.  Tick the appropriate boxes, restart again, and IIRC they should automount without having to edit /etc/fstab.

Auto mount Windows disks
Fire up a terminal, to do this click Applications > Accessories > Terminal
Then type (or copy/paste) the following - 1 line at a time
```

sudo aptitude update
sudo aptitude install ntfs-config
```
Ok so when that returns you to user@pcname, that should be installed                 

Next, make sure you have NO drives mounted (they'll usually appear on your desktop). If you have disks mounted, right-click the icons (one by one) and choose unmount.
They also appear when opening Nautilus.
Then run the program from System > Administration > NTFS Configuration Tool

Enter your password when prompted - and choose the drives that you want to be automounted. Click Apply.

Now simply make sure that "Enable Write Support for Internal Drives" is checked and click OK.

---

### Post by megavolt1 on 2009-06-29
[t4thfavor]("http://ubuntuforums.org/member.php?u=230154"), (and thank-you to the rest of you for providing input.)

That worked mostly. 2 of the 3 drives were mounted automatically. The 3rd one not mounting automatically, although I believe it tried and failed. When I try to mount the 3rd drive manually, I get the following error:

ERROR:
Cannot mount volume.
You are not privileged to mount this problem.

Have I made an error in configuration and/or how do I change permissions to mount the drive?

FSTAB:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=97efa421-875b-4ee8-96c8-c1f53bceb769 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=337deb12-1e65-4c1b-a032-50098bf65ba0 /home           ext3    relatime        0       2
# /dev/sda3
UUID=32ddc3a6-9a18-4f0b-9672-8e9a756af7b0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

# /dev/sdb1 BDF 09.06.28 (Mounted successfully)
UUID=2FB9F68862B8FCE0 /media/disk-1 ntfs-3g
relatime,errors=remount-ro 0 1

# /dev/sdc1 BDF 09.06.28 (Mounted successfully)
UUID=77728C9F1197FA35 /media/disk-2 ntfs-3g
relatime,errors=remount-ro 0 1

# /dev/sdd1 BDF 09.06.28 (Failed to mounted)
UUID=64E849090676DD12 /media/disk-3 ntfs-3g
relatime,errors=remount-ro 0 1

UUID:
root@computer-douglas:/home/brett# ls -lah /dev/disk/by-uuid
total 0
drwxr-xr-x 2 root root 200 2009-06-29 13:09 .
drwxr-xr-x 6 root root 120 2009-06-29 13:09 ..
lrwxrwxrwx 1 root root  10 2009-06-29 13:09 17DF-4276 -> ../../sde1
lrwxrwxrwx 1 root root  10 2009-06-29 13:09 2FB9F68862B8FCE0 -> ../../sdb1
lrwxrwxrwx 1 root root  10 2009-06-29 13:09 32ddc3a6-9a18-4f0b-9672-8e9a756af7b0 -> ../../sda3
lrwxrwxrwx 1 root root  10 2009-06-29 13:09 337deb12-1e65-4c1b-a032-50098bf65ba0 -> ../../sda2
lrwxrwxrwx 1 root root  10 2009-06-29 13:09 4841-A76E -> ../../sdf1
lrwxrwxrwx 1 root root  10 2009-06-29 13:09 64E849090676DD12 -> ../../sdd1
lrwxrwxrwx 1 root root  10 2009-06-29 13:09 77728C9F1197FA35 -> ../../sdc1
lrwxrwxrwx 1 root root  10 2009-06-29 13:09 97efa421-875b-4e

---

### Post by t4thfavor on 2009-06-29
could be dirty, if its ntfs, i usually have to add the force switch to the manual mount. Can't remember it off hand, but it may be a start. Oh, and make sure disk-3 either exists, and is not in use, or exists at all.

If something else is mounted there it may fail.

Also: Did you try rebooting?

---

