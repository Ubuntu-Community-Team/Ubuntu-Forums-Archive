---
title: "Mounting NTFS-partition with read and execute privileges for other users than owner?"
date: 2006-04-14
forum: General Help
---

### Post by lezz on 2006-04-14
Hi

As a normal user in Ubuntu I cant get access to my /dev/hdb1 as its a ntfs-partition. The 'ls -la' output shows:

dr-x------ 1 root root 8192 2006-04-14 20:28 /mnt/hdb1

How do I write in fstab to enable reading the partition for users in the same group and other users when I mount it? Current line is:

/dev/hdb1 /mnt/hdb1 ntfs utf8 1 1

---

### Post by Ramses de Norre on 2006-04-14
Change it to this:
```
/dev/hdb1       /mnt/hdb1  ntfs    nls=utf8,umask=0222 0       0

```

---

### Post by aysiu on 2006-04-14
[http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by xyz on 2006-04-14
Hi aysiu,

I just consulted psychocats.net. Very nice, clear explanation. However, the noob here's a bit confused. Does not seem my fstab 'looks' right. I'd like to post it here and if you have a minute to look at it, I'd greatly appriciate it. Thanks in adv.
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1 
/dev/hda1       /media/hda1 /windows ntfs nls=utf8,umask=0222 0 0    
/dev/hda5       /media/hda5     ntfs    defaults        0       0
/dev/hda6       none            swap    sw 0 0             0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


When I run:
```
sudo mount -a
```
it says:
> [mntent]: line 6 in /etc/fstab is bad


OK I'll take a guess! Do I have to make this line
> /dev/hda5       /media/hda5     ntfs    defaults        0       0

look the same as /dev/hda1...?

---

### Post by lezz on 2006-04-14
Thx a lot!

Now I wonder this: What is the first digit symbolizing in umask=0222? From the right end we first have others, then group and then the owner. But who is the zero?

---

### Post by aysiu on 2006-04-14
This is line 6: ```
/dev/hda1 /media/hda1 /windows ntfs nls=utf8,umask=0222 0 0 
``` and it's bad because it has two mount points.

The syntax goes:

physical_location mount_point filesystem_type mount_options

What you have is:

physical_location mount_point mount_point filesystem_type mount_options

It can't be mounted at both /media/hda1 **and** /windows

---

