---
title: "Disk 100% full"
date: 2011-03-08
forum: General Help
---

### Post by HarderThanYouThink on 2011-03-08
server crashed , restarted and apache wouldn't start , nor would ftp or ispcp , i believe it is because of disk full

Filesystem            Size  Used Avail Use% Mounted on
/dev/vda1             6.1G  6.1G     0 100% /
none                  498M  208K  497M   1% /dev
none                  502M     0  502M   0% /dev/shm
none                  502M   84K  502M   1% /var/run
none                  502M     0  502M   0% /var/lock
none                  502M     0  502M   0% /lib/init/rw
/dev/vdb1             459G  6.0G  430G   2% /home

i got lots of space on vdb1 , how do i give vda1 space

---

### Post by HereInOz on 2011-03-08
You could try changing the partition sizes with a GParted boot CD.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by HereInOz on 2011-03-08
Sorry, that won't work - only one partition on that disk.  Sorry for misleading you.

---

### Post by HereInOz on 2011-03-08
You could get a bigger HDD, clone the system to that larger HDD, then use GParted to expand the 6.1GB partition in to the rest of the larger hard disk.

That'll work.

---

### Post by Sazhen86 on 2011-03-08
Hi

You could move some of the file systems from vda1 to vdb1 and add entries to the fstab to mount them from there.  

You'd need to shrink the /home partition on vdb1 and create a new partition for, say, /usr and copy the whole of /usr from vda1 to vdb1, delete the contents of /usr on vda1 leaving an empty directory for the mount point and add an entry to the fstab for the new /usr partition.

Cheers

---

