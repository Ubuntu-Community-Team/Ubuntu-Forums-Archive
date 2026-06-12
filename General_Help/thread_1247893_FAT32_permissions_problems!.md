---
title: "FAT32 permissions problems!"
date: 2009-08-23
forum: General Help
---

### Post by turinturambar on 2009-08-23
I have a dell laptop with three partitions:

Windows
File storage (FAT32)
Ubuntu

I'm having problems with my file storage partition.
Every time I restart I have had to open a sudo nautilus window, unmount the partition, and change permissions and owners so that I can write and delete files and folders.  This seems to have worked for a while, but now, although I can make folders, I cannot delete them and I can't make or delete files.  If I try to change the permissions, it claims it's a read-only file system.  What am I doing wrong?  Please help.

Thanks.

---

### Post by tomasrey88 on 2009-08-23
> **turinturambar said:**
> I have a dell laptop with three partitions:

Windows
File storage (FAT32)
Ubuntu

I'm having problems with my file storage partition.
Every time I restart I have had to open a sudo nautilus window, unmount the partition, and change permissions and owners so that I can write and delete files and folders.  This seems to have worked for a while, but now, although I can make folders, I cannot delete them and I can't make or delete files.  If I try to change the permissions, it claims it's a read-only file system.  What am I doing wrong?  Please help.

Thanks.

[B]This might be a bug because I've found dozens of thread with this problem. Please, Mods, fix the bug and/or let us know what the solution is. Thanks. I invite you to visit my post for further details: 
[/B][http://ubuntuforums.org/showthread.php?t=1247804](http://ubuntuforums.org/showthread.php?t=1247804)

---

### Post by michy99 on 2009-08-23
Post your fstab file.```
cat /etc/fstab
```

---

### Post by DeMus on 2009-08-23
> **turinturambar said:**
> I have a dell laptop with three partitions:

Windows
File storage (FAT32)
Ubuntu

I'm having problems with my file storage partition.
Every time I restart I have had to open a sudo nautilus window, unmount the partition, and change permissions and owners so that I can write and delete files and folders.  This seems to have worked for a while, but now, although I can make folders, I cannot delete them and I can't make or delete files.  If I try to change the permissions, it claims it's a read-only file system.  What am I doing wrong?  Please help.

Thanks.

Which Windows do you have installed? Is it XP or later? If so, boot Windows and open a terminal ( Start, "Run a command", type cmd in the input box and click OK).
Type: convert driveletter: /fs:ntfs

Then do this:

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
Then type fat2ntfs

---

### Post by nikhilbhardwaj on 2009-08-23
```

/dev/sdb7  /mnt/Games  vfat uid=1000,gid=1000,dmask=027,fmask=137,umask=000  0  0

```
replace the device mount point and uid and gid with your own for the partition that's troubling you

if you want the exact line then post
the output of 
sudo fdisk -l
cat /etc/fstab

---

### Post by turinturambar on 2009-08-23
@ DeMus:
Is that a fix for the windows partition or my file storage partition?  I'm not having any problems with the ntfs windows partition, (it's XP, by the way) I'm just having the problem with my FAT32 partition.

Result of: cat /etc/fstab

```
 /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# / was on /dev/sda5 during installation
UUID=b9d7229b-be98-4a29-aa78-343f82b1394c  /              ext3         relatime,errors=remount-ro  0  1  
# swap was on /dev/sda3 during installation
UUID=cc8852e0-7b8a-41db-b632-15c3d3e4b84d  none           swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/sdb1                                  /media/sdb1    vfat         auto,user,rw                0  0  
/dev/sda6                                  /media/sda6    vfat         auto,user,rw               0  0  
```

@ Nikhil...
Could you tell me what those commands do?

Thank you all.

---

### Post by loomsen on 2009-08-23
> **loomsen said:**
> Hello.

You need to add a line to your /etc/fstab to define defaults for FAT32 devices. This could look something like

```

#DEVICE     MNT-POINT    FS-TYPE      OPTIONS
/dev/usb  /mnt/usb        vfat       rw,user  0 0

```

This would grant permissions to all users to (un-)mount $DEVICE with given $OPTIONS at given $MNT-POINT

Just stumbled upon...

gconf-editor

browse to 
system &#8594; storage &#8594; default_options &#8594; vfat

and add your options there

Just answered this to another post.

> Could you tell me what those commands do?

fdisk: tool to manipulate disks (format, relabel, resize, manage flags etc)  
fdisk -l: list available disks

cat: concatenate files and print to stdout (dump a file to stdout, "read" the file)
/etc/fstab:  /etc is a system folder containing configurations,
fstab: filesystem tab (which fs shall be mounted where using which options)

cat /etc/fstab : prints your current config

---

### Post by turinturambar on 2009-08-23
In my fstab, it lists sda6 (my file storage partition) as being auto,user,rw.  On yours, it doesn't have auto.  If I delete that will it fix it possibly?

And as for editing it through gconf-editor, I do not know what to change any of those options to.  Does anyone know?

Thank you much all.

---

