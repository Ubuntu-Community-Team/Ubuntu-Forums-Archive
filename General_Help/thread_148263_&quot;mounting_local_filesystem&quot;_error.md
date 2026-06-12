---
title: "&quot;mounting local filesystem&quot; error"
date: 2006-03-21
forum: General Help
---

### Post by Fedcer on 2006-03-21
Hi!, I've just installed Ubuntu and at startup I get this this message:

mounting local filesystem......failed

Any idea of what it is and what could I do? (I've searched in the froums but I haven't found a clear answer).


Here it is my /etc/fstab:


# /etc/fstab: static file system information
#
# <file system> <mount point> <type> <options> <dump> <pass>

proc	/proc	proc	defaults	0	0
/dev/hda3		/	ext3	defaults,errors=remount-ro	0	1
/dev/hda6		/home	ext3	defaults	0	2
/dev/hda1		/media/hda1	ntfs	defaults	0	0
/dev/hdb1		/media/hdb1	ntfs	defaults	0	0
/dev/hdb5		/media/hdb5	ntfs	defaults	0	0
/dev/hdb6		/media/hdb6	ntfs	defaults	0	0
/dev/hdb7		/media/hdb7	ntfs	defaults	0	0
/dev/sda1		/media/sda1	vfat	defaults	0	0
/dev/hda5		none		swap	sw	0	0
/dev/hdd		/media/cdrom0	udf,iso9660    user,noauto	  0	0
/dev/hdc		/media/cdrom1	udf,iso9660    user,noauto	  0	0
/dev/scd0		/media/cdrom2	udf,iso9660    user,noauto	  0	0
/dev/fd0		/media/floppy0	auto    rw,user,noauto	  0	0


And this is the result of the "mount" command:


/dev/hda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tempfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-9-386/volatile type tmpfs (rw,mode=0755)
/dev/hda6 on /home type ext3 (rw)
/dev/hda1 on /media/hda1 type ntfs (rw)
/dev/hdb1 on /media/hdb1 type ntfs (rw)
/dev/hdb5 on /media/hdb5 type ntfs (rw)
/dev/hdb6 on /media/hdb6 type ntfs (rw)
/dev/hdb7 on /media/hdb7 type ntfs (rw)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)

Thank you !!!

---

### Post by taurus on 2006-03-21
Looks like the error comes from the line "/dev/sda1 /media/sda1 vfat defaults 0 0" then.  Is that a removable USB drive or something?

---

### Post by babygigi on 2006-03-21
oh i've gotten that too lately... it boots perfectly though...

---

### Post by Fedcer on 2006-03-21
[QUOTE=taurus]Looks like the error comes from the line "/dev/sda1 /media/sda1 vfat defaults 0 0" then.  Is that a removable USB drive or something?[/QUOTE]

Hi. Yes it is a USB hard drive.

I tried to open it and a message appeared saying that it was unable to mount the disk. So, thorught the terminal I logged as root and mounted it manually.

Now it is working and the message doesn't display any more!

Thanks, for the help.

---

