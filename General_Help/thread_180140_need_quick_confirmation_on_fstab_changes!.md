---
title: "need quick confirmation on fstab changes!"
date: 2006-05-21
forum: General Help
---

### Post by starkes on 2006-05-21
Hey

I'm running ubuntu off of an 80gb drive, and i just realized it has been set to slave this whole time. I guess this wouldnt be a problem, but now I want to add a 300gb drive for space, but if i set the original drive to master and the new 300gb drive to slave, it wont boot. 

If i set things the other way around with the 300gb as master and the 80gb drive as slave, it tries to boot into a partition i have on the 300gb drive with suse on it (which i am going to remove, btw)

I want to have my primary hard drive be the master, and the new 300gb drive be the slave, so i can just mount it somewhere.

I checked out my fstab and noticed that everything for this current drive says hdb instead of hda. Is this because it is set to slave instead of master?

This is my current /etc/fstab

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb3       /serve          ext3    defaults        0       2
/dev/hdb2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

If I set my current 80gb drive to master and change my /etc/fstab to this (replacing hdb's with hda's), will it boot?

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /serve          ext3    defaults        0       2
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

Hopefully someone out there can confirm that this will work (or not) before i just go do it and hope for the best!

---

### Post by Jussi Kukkonen on 2006-05-21
I'm not going to promise anything, just wanted to remind that you'll probably need to muck with /boot/grub/menu.lst too... Of course you can try that stuff at boot time too.

---

### Post by starkes on 2006-05-21
thanks for reminding me, i probably would have forgot about that. hehe.

Alright im just going for it...

---

### Post by starkes on 2006-05-21
ok well theres a nice lesson for anyone who wants to switch a slave drive to a master, you need to edit /etc/fstab AND /boot/grub/menu.lst

change the hdb's to hda's and it works

---

### Post by starkes on 2006-05-22
hmm, now can anyone tell me why when i try to boot my 80gb drive up with my new 300gb as a slave, it hangs after the boot loader is done and ubuntu is starting up?

just how would one format an extra drive and set it all up without using the utility in the installer?

---

