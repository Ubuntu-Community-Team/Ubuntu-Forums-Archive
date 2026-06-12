---
title: "fresh 9.10 install wiped out my DVD"
date: 2010-03-04
forum: General Help
---

### Post by harryliddic on 2010-03-04
I had to do a fresh install of 9.10 because the update version from the update manager made 9.10 crash. Since then everything as gone well except for my dvd/cdrom The cd part of it works but the dvd doesn't and since I use linux for video editing it has put a hitch in my get-along. I was recommend this code
```
sudo mount -o loop /dev/sr0 /media/cdrom
```

But that returned
```
harry@harry-desktop:~$ 'sudo mount -o loop /dev/sr0 /media/cdrom'
bash: sudo mount -o loop /dev/sr0 /media/cdrom: No such file or directory
```

My fstab looks like this
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=a543ee9d-d941-4bc2-8ca7-c3700d7bd70b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=e2690653-bf6f-4bf2-be00-45b0a5c58a47 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/dvd	/media/dvd	auto    rw,user,noauto,exec,utf8 0        0
```

Plese only people from the A list should repond that means "A"nybody.

---

### Post by lavinog on 2010-03-05
```
harry@harry-desktop:~$ 'sudo mount -o loop /dev/sr0 /media/cdrom'
bash: sudo mount -o loop /dev/sr0 /media/cdrom: No such file or directory
```

It looks like the problem here was the single quotes
try this instead:
```
sudo mount -o loop /dev/sr0 /media/cdrom
```

---

### Post by lavinog on 2010-03-05
Also after the update crashed, did you try restarting one more time?
If it happens again, restart and see if it boots fine the second time...if it does, uninstall ureadahead.

---

### Post by harryliddic on 2010-03-05
I tried withou the quotes and recieved this

```
harry@harry-desktop:~$ sudo mount -o loop /dev/sr0 /media/cdrom
[sudo] password for harry: 
/dev/sr0: No medium found
harry@harry-desktop:~$ 


```


what is /dev/sr0 anyway?  should I try an iso #  in the fstab what ever that would be?

my most common error message is> Media file: No /dev/dvd exits

---

### Post by harryliddic on 2010-03-05
the update is history ,I chose a fresh install with new partitions at the advice of a forum member.

---

### Post by harryliddic on 2010-03-05
I need to activate /dev/dvd because I need to use qdvdauthor this weekend and that program is filled with commands to /dev/dvd. The project is due out monday and I don't have time to do it in windows

---

### Post by lavinog on 2010-03-06
/dev/sr0 should normally be symlinked to /dev/dvd# (where # is a number, and usually 1)
This was a change from /dev/dvd at some point, and some programs still might be referencing the /dev/dvd.  If this is the case you should be able to create it yourself:
```

sudo cp -s /dev/sr0 /dev/dvd

```
It will also help to check what exists in /dev first...in case it isn't sr0 for you.

---

