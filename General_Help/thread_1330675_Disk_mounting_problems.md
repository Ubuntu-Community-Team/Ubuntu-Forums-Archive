---
title: "Disk mounting problems"
date: 2009-11-18
forum: General Help
---

### Post by emigrant on 2009-11-18
hi all,
i have two problems with mounting disks:


[LIST=1]
[*]i have 4 users in my system, and me (sudoer) have access to the ntfs drives. but other users don't have access to them unless i already have clicked them.
[*]USB drives are not accessible to users except the original user who plugged it in. it is not accessible even for the sudoer.
[/LIST]

helps would be greatly appreciated.
thank you very much:popcorn:

PS:
```

$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x03550354

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6375    51200000    7  HPFS/NTFS
/dev/sda2            6375       11474    40960000    7  HPFS/NTFS
/dev/sda3           11475       11499      200812+  82  Linux swap / Solaris
/dev/sda4           11500       19457    63922635    5  Extended
/dev/sda5           11500       19170    61617276   83  Linux
/dev/sda6           19437       19457      168651   82  Linux swap / Solaris
/dev/sda7           19171       19436     2136613+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 4022 MB, 4022337536 bytes
255 heads, 63 sectors/track, 489 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x83f5fd0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         460     3694918+   b  W95 FAT32
/dev/sdb2             461         489      232942+   5  Extended
/dev/sdb5             461         489      232911   82  Linux swap / Solaris

```

fstab;

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=becef1b2-d864-4764-828f-6381e90fd95d /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=bd49a241-1650-4369-82ae-726b389bc10c none            swap    sw              0       0
# swap was on /dev/sda6 during installation
UUID=2c7425b6-d64e-d288-ae82-bf2580cd63c4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

---

### Post by Giblet5 on 2009-11-18
You can make the NTFS drives mountable by users by adding entries to /etc/fstab like

```
/dev/sda1  /media/C  ntfs  rw,noauto,user,noatime,noexec,utf8  0  0
/dev/sda2  /media/D  ntfs  rw,noauto,user,noatime,noexec,utf8  0  0
```

Your wish for USB drives is not possible. There is no way for the computer to know which user inserted the device, plus there is no way to prevent a sudoer from seeing whatever they want to see, without restricting the sudoer to specific commands.

---

### Post by emigrant on 2009-11-18
thanks buddy, i mounted the two partitions to /mnt/ and it worked but the 'disk' icons didn't appear.
then again i mounted them to /media/ and the disk icons appeared on the desktop.
so now i have another question.

why the heck is the /mnt directory available? :mad:

---

### Post by emigrant on 2009-11-18
one more question.
i created a seperate directory in /media and named it Pendrive and mounted the USB there. despite the fact there is already a directory for the USB where its been mounted. 
my question is why i cannot access the Pendrive directory from the other accounts?

---

### Post by Giblet5 on 2009-11-18
Well, do some leg work.

Unmount the pendrive and do ```
ls -l /media
```

Is the mountpoint accessible by all users (drwxrwxrwx)? If not, then you can change that by unmounting the device and running ```
sudo chmod 777 /media/directoryname
``` then remounting the device.

Note: execute permission on a directory does not mean that files under that directory are necessarily executable. It just means users can change their working directory to that directory.

You can also see what the kernel actually did to mount something via ```
cat /etc/mtab
``` and examining the mount options used. If it has a .....,user=bob... and you're bob, then only you can unmount it.

---

### Post by emigrant on 2009-11-18
hi, thank you for your continuous help.
the problem is if i see the permission while the drive is mounted it has different permission, and without mounted it has another set of permissions :(

below the codes for clarity:

```
drwxrwxrwx  1 root   root 24576 2009-11-18 18:42 Cdrive
lrwxrwxrwx  1 root   root     6 2009-10-22 03:17 cdrom -> cdrom0
drwxr-xr-x  2 root   root  4096 2009-10-22 03:17 cdrom0
drwxrwxrwx  1 root   root  8192 2009-11-17 21:34 Ddrive
drwx------ 15 emigrant root  4096 1970-01-01 05:30 disk
lrwxrwxrwx  1 root   root     7 2009-10-22 03:17 floppy -> floppy0
drwxr-xr-x  2 root   root  4096 2009-10-22 03:17 floppy0
drwx------ 15 emigrant root  4096 1970-01-01 05:30 Pendrive
emigrant@emigrant-desktop:/media$ sudo umount Pendrive/
emigrant@emigrant-desktop:/media$ ls -l
total 48
drwxrwxrwx  1 root   root 24576 2009-11-18 18:42 Cdrive
lrwxrwxrwx  1 root   root     6 2009-10-22 03:17 cdrom -> cdrom0
drwxr-xr-x  2 root   root  4096 2009-10-22 03:17 cdrom0
drwxrwxrwx  1 root   root  8192 2009-11-17 21:34 Ddrive
drwx------ 15 arshad root  4096 1970-01-01 05:30 disk
lrwxrwxrwx  1 root   root     7 2009-10-22 03:17 floppy -> floppy0
drwxr-xr-x  2 root   root  4096 2009-10-22 03:17 floppy0
drwxr-xr-x  2 root   root  4096 2009-11-19 02:38 Pendrive
```

and this is at /etc/mtab

```
/dev/sda5 / ext4 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
/dev/sdb1 /media/disk vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0
/dev/sda1 /media/Cdrive fuseblk ro,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0
/dev/sda2 /media/Ddrive fuseblk ro,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0
```

---

### Post by Giblet5 on 2009-11-18
Well, we're making progress, right?

Let's create an fstab entry for the Pendrive.

With the pen drive mounted, see if you can figure out what the UUID of the pen drive is via the following command

```
ls -l /dev/disk/by-uuid
```

Select and copy the UUID for the pen drive, then create an entry in /etc/fstab:
```
UUID=[COLOR="DarkRed"]xxxxxxxxxxxxxxxxxxxxxxxxxxx[/COLOR] /media/Pendrive vfat rw,dmask=0777,fmask=0666,noauto,noatime,users,nls=utf8 0 0
```

where the red text is replaced by the UUID of the pen drive.

Then unmount the pen drive explicitly. Then run ```
sudo mount -a
```

Does that look better?

You can look up the available mount options via ```
man mount
``` I may not have chosen optimal options, but it will be in the ballpark....somewhere.

---

### Post by emigrant on 2009-11-18
Thanks buddy for the help. It seems ok now.
The problem i think was because in the fstab entry for Pendrive instead of users iv given user. Sorry that i cannot paste the entry here as im writing this from mobile.
Thank you very much for your time and help. Much appreciated :)

---

