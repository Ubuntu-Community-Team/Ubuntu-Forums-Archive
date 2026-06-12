---
title: "Cant change permissions on fat32 partition"
date: 2006-04-21
forum: General Help
---

### Post by mental_drummer on 2006-04-21
Hi everyone,
Tried looking on loads of forums - lots of people with same problem as me but their solutions dont seem to work! ive got windows XP on the primary hard drive and linux on the secondary drive. I created a fat32 patition on the windows hard disk to use as a swap between windows and linux. windows can access it fine - i can write files to the partition from windows and read and execute them from linux but i cant write from linux. ive even tried logging in as root to gnome and changing the permissions on /overflow in the properties but it tells me i cant!

Here's my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdc	/media/cdrom0   	iso9660  ro,user 	0 	0
/dev/hda1	/media/windows  ntfs  	iocharset=utf8,umask=0227  0    0
/dev/hda2	/overflow	vfat 	iocharset=utf8,umask=000 0 0 

thanks in advance for any help u can give me
](*,)  <- hehe nice smilie - pretty much sums it up

---

### Post by Anilkumar on 2006-04-21
Ok did u unmount u r windows partitions?

---

### Post by tonyr on 2006-04-21
I assume you're talking about **/dev/hda2 /overflow vfat**.  Try this:
```

/dev/hda2 /overflow vfat **defaults**,iocharset=utf8,umask=000 0 0 

```
which should set access to **rw** instead of **ro.**  You may have to
explicitly use rw in the options list.
```

/dev/hda2 /overflow vfat defaults,**rw**,iocharset=utf8,umask=000 0 0 

```

---

### Post by Ramses de Norre on 2006-04-21
Set umask to 0000 instead of 000. The other options are ok.

---

### Post by mental_drummer on 2006-04-22
Hi,
Thank very much everyone
Changed 000 to 0000 and, lo and behold, it worked! I thought i had tried that but apperently not. 
Thanks for your help

---

