---
title: "Reset during upgrade HELP -  GLIBC_2.14 not found"
date: 2012-04-30
forum: General Help
---

### Post by geekyhawkes on 2012-04-30
I was upgrading my xubuntu machine and during the install it rebooted (no idea why), when it started back up i get the following:

mountall: /lib/x86_64-linux-gnu/libc.so.6: version GLIBC_2.14 not found.

Ive searched around and it would seem i can fix it with a live cd and copy across the missing file, problem is the drives weere on mdadm RAID and ive no idea how to get the raid back up after booting the live cd.  

Ive tried mdadm --detail /dev/md0 but of course it comes back file not found, likewise if i try ls -l /dev/md i get nothing as the Live cd install doesnt have any knowledge of my raid.

Whats the mdadm equivilant to mount /dev/sda1?  Anyone help me please?  Im pretty sure my RAID stripe was built as /dev/md0 and the install spread accross the 2 drives.  I have the GRUB partition on a seperate 1GB partition which i do have access to if that helps?

Thanks for all, all help! 

A Very desperate ;

ANDY

---

### Post by geekyhawkes on 2012-05-01
So i also tried booting recovery on an old kernel and then apt-get dist-upgrade but i get an error saying 

Not using locking for read only file system, dpkg interupted use dpkg --configure -a

If i try dpkg --configure -a i get an error saying

Dpkg error: unable to access dpkg status area: read only file system

Edit: with some help im getting closer: mount -o remount,rw / gets rid of the read only error for dpkg.

---

### Post by geekyhawkes on 2012-05-01
In case anyone searches for the same problem here is how far i have got so far : 

[http://www.linuxquestions.org/questions/showthread.php?p=4667309#post4667309](http://www.linuxquestions.org/questions/showthread.php?p=4667309#post4667309)
If ypu got here from a search click the link above : solved!

---

