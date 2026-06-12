---
title: "Cannot mount the CD after ugrading to Breezy"
date: 2006-05-07
forum: General Help
---

### Post by ozorba on 2006-05-07
I have been using hoary for a while on another system and the CD was working fine.
after I ugraded to Breezy my cd does not work.

I did cat /proc/devices and got the following:

nodev   sysfs
nodev   rootfs
nodev   bdev
nodev   proc
nodev   sockfs
nodev   pipefs
nodev   futexfs
nodev   tmpfs
nodev   inotifyfs
nodev   eventpollfs
nodev   devpts
        cramfs
nodev   ramfs
nodev   devfs
nodev   mqueue
nodev   usbfs
        ext3
        udf
        iso9660

and my /etc/fstab is:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


When I insert my data CD the cd turns and stops. When I try to see what it has I get nothing.

If I type

mount /media/cdrom0

I get 

mount: No medium found

Even if I do

 sudo mount -t iso9660 -r /dev/cdrom /media/cdrom0

I get 
mount: No medium found

Any suggestions?

BTW: USB CD-RW works fine.

---

