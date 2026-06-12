---
title: "Mount NTFS drive for other user problem"
date: 2010-05-05
forum: General Help
---

### Post by G-Sun on 2010-05-05
Hi!
I have a ntfs-partition that I will use for documents for me and another user.
I works fine for me.
The partition is mounted and I can read/write.

However, for the other user the partition i snot showing up.
What to do?

I've tried changing the permissions from nautilus, but no success.

---

### Post by gzarkadas on 2010-05-05
Check that the account in question has the right 'Mount user-space filesystems (FUSE)' checked. This is in menu {System|Users and Groups|tab User Rights} (at least in Karmic).

Also post here the output of ```
cat /etc/group|grep -P '<account1>|<account2>'
``` where <account?> must be replaced by the login names of the two accounts.

Do you mount your drive by the Places menu, or with an /etc/fstab entry?

---

### Post by G-Sun on 2010-05-05
> **gzarkadas said:**
> Check that the account in question has the right 'Mount user-space filesystems (FUSE)' checked. This is in menu {System|Users and Groups|tab User Rights} (at least in Karmic).

Also post here the output of ```
cat /etc/group|grep -P '<account1>|<account2>'
``` where <account?> must be replaced by the login names of the two accounts.

Do you mount your drive by the Places menu, or with an /etc/fstab entry?
Thanks!
'Mount user-space filsystems (FUSE)' is checked

```
geir@Sol:~$ cat /etc/group|grep -P 'geir|tone'
adm:x:4:geir,tone
dialout:x:20:geir,tone
fax:x:21:tone
cdrom:x:24:geir,tone
floppy:x:25:tone
tape:x:26:tone
dip:x:30:tone
video:x:44:tone
plugdev:x:46:geir,tone
fuse:x:104:tone
lpadmin:x:105:geir
admin:x:119:geir
nopasswdlogin:x:121:tone,geir
geir:x:1000:
sambashare:x:122:geir
tone:x:1001:

```

---

### Post by dino99 on 2010-05-05
can tweak your devices and partitions with mountmanager

---

### Post by G-Sun on 2010-05-05
Thanks!
Installed mountmanager and granted everyone access to the partition.
When accessing the partition from tone-user
I've got this:
```
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
http://ntfs-3g.org/support.html#unprivileged
```

---

### Post by gzarkadas on 2010-05-05
I don't have this type of problem in my 9.10 system; I just created a file and wrote to it inside an ntfs partition created by gparted onto a usb stick - from an unprivileged account. The disk was auto-mounted when inserted.

Check whether:

1. {System|Administration|Users and Groups|tab User Rights|Option Automatic Access to External Storage Devices} or something like this (I see a localised version) is checked for the unprivileged account.

2. You have installed the packages:
[INDENT]ntfs-3g
libntfs-3g54
libntfs10
ntfsprog
libgnomevfs2-0
fuse-utils
gvfs
gvfs-fuse
gvfs-bin
gvfs-backends
[/INDENT](the versions may be higher in Lucid Lynx, I don't know since I have not installed it). If not, try to install them and see if the issue gets fixed.

---

### Post by Morbius1 on 2010-05-05
Why not share with us some facts. Please post the output of the following commands:

Open **Terminal**
Type **sudo blkid -c /dev/null**
Type **cat /etc/fstab**
Type **mount**

---

### Post by G-Sun on 2010-05-05
> **gzarkadas said:**
> 

2. You have installed the packages:[INDENT]ntfs-3g
libntfs-3g54
libntfs10
ntfsprog
libgnomevfs2-0
fuse-utils
gvfs
gvfs-fuse
gvfs-bin
gvfs-backends
[/INDENT]
Thanks! They're all installed, except libntfs-3g54

---

### Post by G-Sun on 2010-05-05
> **Morbius1 said:**
> Why not share with us some facts. Please post the output of the following commands:

Open **Terminal**
Type **sudo blkid -c /dev/null**
Type **cat /etc/fstab**
Type **mount**
:)
```
geir@Sol:~$ sudo blkid -c /dev/null
/dev/sda1: LABEL="Ubuntu" UUID="0d033f52-5aa8-48d5-bfd8-798adbdfcb79" TYPE="ext3" 
/dev/sda2: LABEL="XP" UUID="1865969E6DC00666" TYPE="ntfs" 
/dev/sda4: UUID="306d6604-e241-4e65-aa95-2091e8433130" TYPE="swap" 
/dev/sda5: LABEL="Lagerhall" UUID="B220A1F220A1BDAB" TYPE="ntfs" 
/dev/sdb1: LABEL="Disko" UUID="E45CA1925CA16052" TYPE="ntfs" 
/dev/sdb5: LABEL="Enriche" UUID="A82CA5E92CA5B2AC" TYPE="ntfs" 
/dev/sdb6: LABEL="Fritz" UUID="8CA4AA73A4AA5F86" TYPE="ntfs" 

``````
geir@Sol:~$ cat /etc/fstab
/dev/fd0 /media/floppy0 vfat noauto 0 0
UUID=0d033f52-5aa8-48d5-bfd8-798adbdfcb79 / ext3 defaults 0 1
UUID=306d6604-e241-4e65-aa95-2091e8433130 swap swap sw 0 0
UUID=B220A1F220A1BDAB /media/Lagerhall ntfs-3g users 0 0

``````
geir@Sol:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
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
/dev/sda5 on /media/Lagerhall type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
gvfs-fuse-daemon on /home/tone/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=tone)
gvfs-fuse-daemon on /home/geir/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=geir)

```

---

### Post by Morbius1 on 2010-05-05
In a Terminal type:
```
gksu gedit /etc/fstab
```Change this:
> UUID=B220A1F220A1BDAB /media/Lagerhall ntfs-3g users 0 0To this:
```
UUID=B220A1F220A1BDAB /media/Lagerhall ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 0 
```**umask=007** will allow owner ( root ) and group (46 ) to read and write to the partition.
**gid=46** represents group=plugdev. All local login users are members of the plugdev goup by default.

Together this will mount an NTFS partition with owner = root and read / write access to all local login users.

When you're done with the changes save fstab, exit gedit, and back in the terminal type:
```
sudo umount /media/Lagerhall
sudo mount -a

```

---

### Post by G-Sun on 2010-05-06
> **Morbius1 said:**
> In a Terminal type:
```
gksu gedit /etc/fstab
```Change this:
To this:
```
UUID=B220A1F220A1BDAB /media/Lagerhall ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 0 
```**umask=007** will allow owner ( root ) and group (46 ) to read and write to the partition.
**gid=46** represents group=plugdev. All local login users are members of the plugdev goup by default.

Together this will mount an NTFS partition with owner = root and read / write access to all local login users.

When you're done with the changes save fstab, exit gedit, and back in the terminal type:
```
sudo umount /media/Lagerhall
sudo mount -a

```
Thanks!
```
geir@Sol:~$ gksu gedit /etc/fstab
geir@Sol:~$ sudo umount /media/Lagerhall
gs7267: command not found
geir@Sol:~$ sudo mount -a
fuse: failed to access mountpoint /media/Lagerhall: No such file or directory

```
So, undid changes in fstab

---

### Post by G-Sun on 2010-05-06
Ok, now I can't mount from either user..

fstab:
```
/dev/fd0 /media/floppy0 vfat noauto 0 0
UUID=0d033f52-5aa8-48d5-bfd8-798adbdfcb79 / ext3 defaults 0 1
UUID=306d6604-e241-4e65-aa95-2091e8433130 swap swap sw 0 0
UUID=B220A1F220A1BDAB /media/Lagerhall ntfs-3g users 0 0
```

---

### Post by Morbius1 on 2010-05-06
Based on your last posts you didn't make any changes to fstab and your mount point doesn't exist so there's nothing to mount to.

*** STEP 1: Create a mount point for your NTFS partition to live in:***

Open Terminal and type:
```
sudo mkdir /media/Lagerhall
```***STEP 2: Comment out your existing ntfs line in fstab and add a new one:***

In the Terminal type:
> gksu gedit /etc/fstabPlace a # in front of the existing ntfs line untill your fstab file looks like this:
> /dev/fd0 /media/floppy0 vfat noauto 0 0
UUID=0d033f52-5aa8-48d5-bfd8-798adbdfcb79 / ext3 defaults 0 1
UUID=306d6604-e241-4e65-aa95-2091e8433130 swap swap sw 0 0
#UUID=B220A1F220A1BDAB /media/Lagerhall ntfs-3g users 0 0Now add the following line to the end of fstab:
```
UUID=B220A1F220A1BDAB /media/Lagerhall ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 0
```[I][B]STEP 3: Verify that your fstab now looks like this:

[/B][/I]> /dev/fd0 /media/floppy0 vfat noauto 0 0
UUID=0d033f52-5aa8-48d5-bfd8-798adbdfcb79 / ext3 defaults 0 1
UUID=306d6604-e241-4e65-aa95-2091e8433130 swap swap sw 0 0
#UUID=B220A1F220A1BDAB /media/Lagerhall ntfs-3g users 0 0
UUID=B220A1F220A1BDAB /media/Lagerhall ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 0***STEP 4: Save the file and reboot***

Click on "Save" in gedit
Exit gedit
Close Terminal
Reboot

---

### Post by G-Sun on 2010-05-06
> **Morbius1 said:**
> Based on your last posts you didn't make any changes to fstab and your mount point doesn't exist so there's nothing to mount to.

*** STEP 1: Create a mount point for your NTFS partition to live in:***

Open Terminal and type:
```
sudo mkdir /media/Lagerhall
```***STEP 2: Comment out your existing ntfs line in fstab and add a new one:***

In the Terminal type:
Place a # in front of the existing ntfs line untill your fstab file looks like this:
Now add the following line to the end of fstab:
```
UUID=B220A1F220A1BDAB /media/Lagerhall ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 0
```[I][B]STEP 3: Verify that your fstab now looks like this:

[/B][/I]***STEP 4: Save the file and reboot***

Click on "Save" in gedit
Exit gedit
Close Terminal
Reboot

Thanks a lot! I'll do that when I get back to Ubuntu. Maybe the last attempt didn't work because I didn't reboot?

---

