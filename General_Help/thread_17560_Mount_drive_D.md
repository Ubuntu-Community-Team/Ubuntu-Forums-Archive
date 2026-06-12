---
title: "Mount drive D"
date: 2005-03-01
forum: General Help
---

### Post by psyko-lefse on 2005-03-01
I've followed the [UbuntuGuide](http://ubuntuguide.org/) and set it up so my C drive (with windows on) is automaticly mounted at startup ([http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)). But when I tried to mount D drive (which is an extention on the same disc as C) i got this error:
> 
mount: wrong fs type, bad option, bad superblock on /dev/hda3,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
 
Anyone know what I have to do to be able to mount my D drive too?

---

### Post by WillCooke on 2005-03-01
[QUOTE=psyko-lefse]I've followed the [UbuntuGuide](http://ubuntuguide.org/) and set it up so my C drive (with windows on) is automaticly mounted at startup ([http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)). But when I tried to mount D drive (which is an extention on the same disc as C) i got this error:
 
Anyone know what I have to do to be able to mount my D drive too?[/QUOTE]
 I'm assuming that your "D" drive (/dev/hda3) is an NTFS formatted partition?

Try to mount it manually and specify the filesystem:

mount -t ntfs /dev/hdb3 <what ever your mount point is>

If you don't know what your mount point is, try creating a directory called /mnt/ddrive, and then use this as the mount point, so:

mkdir /mnt/ddrive

mount -t ntfs /dev/hda3 /mnt/ddrive

(all this needs to be done as root, so pre-fix the commands with 'sudo')

---

### Post by psyko-lefse on 2005-03-01
I did that, but I still got the same message:

```
elmud@Elmud8600:~ $ sudo mount -t ntfs /dev/hda3 /media/d
mount: wrong fs type, bad option, bad superblock on /dev/hda3,
missing codepage or other error
(aren't you trying to mount an extended partition,
instead of some logical partition inside?)
In some cases useful info is found in syslog - try
dmesg | tail  or so
```


There it says that I'm trying to mount an extended partition istead of some logical partition (which I am trying to). 

I would think that I need to write something a bit different to be able to mount an extended partition, but what?

---

### Post by psyko-lefse on 2005-03-01
Got it sorted. I am apperantly so stupid that I tought D: was on hda3, when it in reality was on hda5 #-o

---

### Post by WillCooke on 2005-03-02
[QUOTE=psyko-lefse]Got it sorted. I am apperantly so stupid that I tought D: was on hda3, when it in reality was on hda5 #-o[/QUOTE]
 That'll do it! :)

---

