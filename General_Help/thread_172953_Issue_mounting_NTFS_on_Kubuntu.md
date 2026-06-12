---
title: "Issue mounting NTFS on Kubuntu"
date: 2006-05-09
forum: General Help
---

### Post by reign on 2006-05-09
Whenever I try to mount my NTFS partitions on Kubuntu, I get a "mount: /dev/hda5 already mounted or /media/hda5 busy" every time. I've tried everything I can think of to get this working but to no avail.

The following is an of
[B]
sudo fdisk -l
cat /etc/fstab
mount | sort[/B]

```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
16 heads, 63 sectors/track, 155061 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           3       42155    21244928    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hda2           42155      155056    56902230    f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/hda5           42155      155056    56902198+   7  HPFS/NTFS

Disk /dev/hdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb2   *           1         951     7638876   83  Linux
/dev/hdb3             952        2434    11912197+   f  W95 Ext'd (LBA)
/dev/hdb5             952         992      329301   82  Linux swap / Solaris
/dev/hdb6             993        2434    11582833+  83  Linux

Disk /dev/sda: 1024 MB, 1024966656 bytes
32 heads, 62 sectors/track, 1009 cylinders
Units = cylinders of 1984 * 512 = 1015808 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   ?      392206      967564   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(392205, 19, 11)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(967563, 8, 51)
Partition 1 does not end on cylinder boundary.
/dev/sda2   ?       85025     1060846   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(85024, 30, 47)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(1060845, 20, 42)
Partition 2 does not end on cylinder boundary.
/dev/sda3   ?      942481     1918302   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(942480, 18, 30)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(1918301, 7, 39)
Partition 3 does not end on cylinder boundary.
/dev/sda4   ?     1454477     1454505       27749+   d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(1454476, 12, 25)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(1454504, 11, 33)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0

/dev/hdb2 / ext3 defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid,nouser 0 1
/dev/hdb6 /home ext3 defaults,atime,auto,rw,dev,exec,suid,nouser 0 2

/dev/hdb5 none swap sw 0 0

/dev/hda1 /media/hda1 ntfs nls=utf8,umask=000,defaults,uid=0,gid=1001,auto,ro,users 0 0
/dev/hda5 /media/hda5 ntfs nls=utf8,umask=000,defaults,uid=0,gid=1001,auto,ro,users 0 0

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0

#/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

/dev/sda        /media/NICK     vfat    rw,user,noauto 0        0
/dev/hdb2 on / type ext3 (rw,errors=remount-ro)
/dev/hdb6 on /home type ext3 (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/sda on /media/NICK type vfat (rw,noexec,nosuid,nodev,user=reign)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /dev/shm type tmpfs (rw)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
usbfs on /proc/bus/usb type usbfs (rw)

```

Please let me know if anyone has any ideas. Thanks!

---

### Post by louis_nichols on 2006-05-09
well... /dev/hda5 IS in your fstab with the auto switch, so it does get mounted at boot time. I'm guessing you can't see it as user, but you'll be able to see it as root. Try editing in fstab the lines with ntfs file systems to have umask=0222

then

umount -a
mount -a

---

### Post by jazzmuzik on 2006-05-09
Maybe hda5 is already mounted?

---

### Post by cyracks on 2006-05-09
I don't know what is with all those errors on /dev/sda but try

$sudo umount /media/NICK
$sudo umount /dev/hda5
$sudo mount /dev/hda5 /media/hda5

if works it should be mounted under /media/hda5

---

### Post by reign on 2006-05-09
the /dev/sda is my usb flash drive. the errors were probbly from when I was setting it up in fstab. That's working fine now, though.

I'm still getting the already mounted or busy errors after trying everything suggested. I'm running a custom kernel for my dual processors if that could have anything to do with it.

Also, what does the "defaults" option do in fstab?

I removed it and still no luck.

I'm going to keep tinkering for a bit. Thanks for the help so far, I didn't expect replies so quick.

---

### Post by cyracks on 2006-05-09
[QUOTE=reign]
Also, what does the "defaults" option do in fstab?
[/QUOTE]

[http://www.google.com/search?hs=h0Z&hl=en&lr=&client=firefox&rls=org.mozilla%3Aen-US%3Aunofficial&q=fstab+defaults&btnG=Search](http://www.google.com/search?hs=h0Z&hl=en&lr=&client=firefox&rls=org.mozilla%3Aen-US%3Aunofficial&q=fstab+defaults&btnG=Search)

---

### Post by cyracks on 2006-05-09
This will show you all processes which are accessing /media/hda5
$lsof -n|grep /media/hda5

To kill all processes connected to a specified path use:
$sudo fuser -k -v -m /media/hda5

and than remount drive. Hope this helps, if not try to look a bug archive if anybody else have the same problem.
[https://launchpad.net/distros/ubuntu/+bugs](https://launchpad.net/distros/ubuntu/+bugs)

---

### Post by jazzmuzik on 2006-05-09
This information may be helpful.

[https://wiki.ubuntu.com/MountNtfsOnBoot?highlight=%28ntfs%29](https://wiki.ubuntu.com/MountNtfsOnBoot?highlight=%28ntfs%29)

It gives an example line for mounting an ntfs drive in /etc/fstab:

/dev/hda2 /mnt/ntfs1 ntfs ro,nls=utf8,umask=0222 0 0

Above, Louis mentioned adding umask=0222. Have you tried that?

---

### Post by transient on 2006-05-13
[QUOTE=reign]Whenever I try to mount my NTFS partitions on Kubuntu, I get a "mount: /dev/hda5 already mounted or /media/hda5 busy" every time.[/QUOTE]

Try /dev/evms/hda5 instead of /dev/hda5 

...
emre

---

### Post by reign on 2006-05-13
[QUOTE=transient]Try /dev/evms/hda5 instead of /dev/hda5 

...
emre[/QUOTE]

That worked! What is /dev/evms/?

Thanks a lot!

---

### Post by transient on 2006-05-14
Glad to hear it worked :)

Well, i had the same problem, i posted the long story here:
[http://ubuntuforums.org/showthread.php?t=175693](http://ubuntuforums.org/showthread.php?t=175693)

.
e

---

