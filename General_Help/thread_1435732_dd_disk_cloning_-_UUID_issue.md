---
title: "dd disk cloning :- UUID issue"
date: 2010-03-21
forum: General Help
---

### Post by nawab on 2010-03-21
Hello users, 

I have a UBUNTU server, recently i cloned the disk using dd and kept the second disk in box itself. yesterday i realized that because of UUID eatures it generated same UUID to my /dev/sdb partitions and it looks like it is using the mix of first disk and second disk. 

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>

proc /proc proc defaults 0 0
# /dev/sda5
UUID=be35a709-c787-4198-a903-d5fdc80ab2f8 / ext3 relatime,errors=remount-ro 0 1
# /dev/sda6
UUID=cee15eca-5b2e-48ad-9735-eae5ac14bc90 none swap sw 0 0

/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

i have RedHat servers as well where i can easily do a dd and keep both disk in server. 
please let me know the workaround for this.

---

### Post by dcstar on 2010-03-21
> **nawab said:**
> Hello users, 

I have a UBUNTU server, recently i cloned the disk using dd and kept the second disk in box itself. yesterday i realized that because of UUID eatures it generated same UUID to my /dev/sdb partitions and it looks like it is using the mix of first disk and second disk. 

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>

proc /proc proc defaults 0 0
# /dev/sda5
UUID=be35a709-c787-4198-a903-d5fdc80ab2f8 / ext3 relatime,errors=remount-ro 0 1
# /dev/sda6
UUID=cee15eca-5b2e-48ad-9735-eae5ac14bc90 none swap sw 0 0

/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

i have RedHat servers as well where i can easily do a dd and keep both disk in server. 
please let me know the workaround for this.

You need to change the UUID of the copied EXT3 partition, do a forum search for detailed instructions.

---

### Post by asmoore82 on 2010-03-21
-OR- you could change the fstab around so that it doesn't use UUID's.

---

### Post by nawab on 2010-03-22
what is the procedure to change in fstab?? please can you point me to a similar document.

---

### Post by soltanis on 2010-03-22
[http://nixcraft.com/shell-scripting/948-change-uuid-ext3-partition.html](http://nixcraft.com/shell-scripting/948-change-uuid-ext3-partition.html)

The second post, the first two code lines which are

```

uuidgen
tune2fs /dev/hdaX -U <generated uuid>

```

Will allow you to change the UUID of your cloned disk.

---

### Post by nawab on 2010-03-22
thanks for the reply. 

is there a way i can do it on live production box? do i need to reboot the box or restart any service after performing this?

---

### Post by Lampi on 2010-03-22
Boot the LiveCD

tune2fs /dev/sdaX -U <generated uuid>

or for a random generated uuid:

tune2fs /dev/sdaX -U random

Then reboot to have the changes take effect

---

