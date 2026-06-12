---
title: "mount dvd drive"
date: 2010-04-22
forum: General Help
---

### Post by majikhotline on 2010-04-22
having trouble mounting a dvd drive; i would like to mount both dvd drive, but dont known how to do it ```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4d7403a1-0983-4231-94ae-3763bf30100e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=831d0f63-0c4f-4abd-aea1-c6b2892aecd0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```Please help

---

### Post by labinnsw on 2010-04-24
Create a directory: (in a terminal type) ```
sudo mkdir /media/cdrom1
``` 

Under ```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
``` in your fstab file, add```
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
```

Again in a terminal type: ```
sudo mount -a
```

---

### Post by majikhotline on 2010-04-27
now i can see the cdrom1, but i get an error window saying mount: special device /dev/scd1 does not exist. I made a directory for /dev/scd1 but the new error is mount: /dev/scd1 is not a block device.......what does that mean?

---

### Post by labinnsw on 2010-04-28
> **majikhotline said:**
> I made a directory for /dev/scd1 but the new error is mount: /dev/scd1 is not a block device.......what does that mean?

You should not make a /dev/scd1 directory. The line with /dev/scd1 in fstab tells the system to mount another device and map it to /media/cdrom1. Browse the /dev directory, have a look around there to get a feel for what goes on in the background. Just look, don't touch. (unless you know what you are doing.)

Looks like the drive is not being recognized. You might want the check if it is _properly_ connected and also that it is in working order. Do you have media in both drives when testing?

---

### Post by majikhotline on 2010-04-28
thank for helping labinnsw, but both dvd burners are on cable select and physical hooked up with the same ribbon.  I looked in the /dev directory and didnt find my entered data of mkdir /dev/scd1. and i have genuine copy of dvds in the drive for testing. I have restarted the computer and getting an error of "mount: special device /dev/scd1 does not exist"

any ideals?

---

### Post by labinnsw on 2010-04-29
Try making one master and the other slave or cable select and slave. When I have more time tomorrow I will look at mine and tell you exactly how I have it set up.

---

### Post by labinnsw on 2010-04-30
OK I have mine set up, master slave. Middle Master, End Slave. Have you noticed the memory aids in there?

---

### Post by majikhotline on 2010-04-30
both of my dvd drives are IDE, what are memory aids?

---

### Post by labinnsw on 2010-05-01
The first memory aid is: 2 words starting with M. Attach the master to the middle slot on the cable. The second is the phrase "Master end Slave" which sounds like "Master and Slave", a common phrase. So the other drive should be attached as slave rather than "cable select" and it should be attached to the end of the cable, not in the middle.

---

