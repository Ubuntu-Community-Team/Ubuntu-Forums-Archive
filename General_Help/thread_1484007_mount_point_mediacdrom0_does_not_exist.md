---
title: "mount point media/cdrom0 does not exist"
date: 2010-05-15
forum: General Help
---

### Post by Rompeprop on 2010-05-15
Than I mount dvd its doing nothing, cant see anything in media/cdrom0 also.
my fstab looks like this :
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=4b6883ba-5e88-4ccb-be90-f8a1ac8434dc /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=aa2ef862-99d6-448b-b2f8-4b467938cd44 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0





sorry, I'm a noob at ubuntu, dont know what to do.

---

### Post by TeoBigusGeekus on 2010-05-15
Open terminal and type
```
sudo mount /dev/scd0
```
Post us any error messages.

---

### Post by Rompeprop on 2010-05-15
mount: special device /dev/scd0 does not exist

---

### Post by Grenage on 2010-05-15
Are you sure the drive is functional?  Can you boot from it?

---

### Post by Rompeprop on 2010-05-15
I'm pretty sure it is. I've had simple cd/rw under ubuntu.. later a friend gave me his dvd/rw, we were installing windows on his old pc before selling it from this cdrom. I connected it, but wasnt using it till today. got to look in to bios.

---

### Post by Grenage on 2010-05-15
It's definitely worth double-checking;  I've seen this quite a few times, and most of them were down to flaky drives.

---

