---
title: "Ubuntu Freezes / Locks - up / non-responsive"
date: 2010-08-30
forum: General Help
---

### Post by Pough913 on 2010-08-30
Hello, 
 I am running Ubuntu 10.04. I have a HP Pavilion Dv7 Laptop, 4GB of ram, An AMD Turion X2 processor, my main HDD is 250GB Samsung and my other internal HDD is a 250GB Western digital. I am Very new to Ubuntu and the forums, So i wish to apologize if this is posted in wrong section. Now on to my problem, While using my computer the screen will go gray(all open windows), and my HDD light stays on. I never had this problem before on my other computer that has Ubuntu on it too. And as i said every window goes gray and the HDD light stays on  and it happens randomly. It will come back to normal some times but others i have to Force Power down.
                                             Thank you!

---

### Post by lisati on 2010-08-31
Duplicate of [http://ubuntuforums.org/showthread.php?t=1564644](http://ubuntuforums.org/showthread.php?t=1564644)
Please don't start multiple threads.

---

### Post by Pough913 on 2010-08-31
Sorry I was just unsure Where this should be posted, Is this the correct place?

---

### Post by varunendra on 2010-08-31
> **Pough913 said:**
> Hello, 
 I am running Ubuntu 10.04. I have a HP Pavilion Dv7 Laptop, [COLOR=Red]**4GB of ram**[/COLOR], An AMD Turion X2 processor, my main HDD is 250GB Samsung and my other internal HDD is a 250GB Western digital.....
....While using my computer the screen will go gray(all open windows), and my HDD light stays on.

With me, it sometimes happens when I use a system with low ram (but  yours is 4GB!!) and try to do something that is memory intensive. So I  guess it happens during swapping of memory to the hard disk. Now unsure  of how to control that, I'd suggest you to check your swap space and  whether a disk is getting out of space. You may post outputs of these-
```
sudo fdisk -l
```
```
df -h
```

---

### Post by Pough913 on 2010-09-04
Ok i just got back on for the first time in a while... 



Ok so "sudo fdisk -l" put out, 


sudo fdisk -l
[sudo] password for patrick: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d08f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29202   234558464   83  Linux
/dev/sda2           29202       30402     9637889    5  Extended
/dev/sda5           29202       30402     9637888   82  Linux swap / Solaris

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004d50c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       15808   126971904   83  Linux








And " df -h"  put out,


[FONT=monospace]Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             221G   65G  145G  32% /
none                  1.4G  332K  1.4G   1% /dev
none                  1.4G  1.6M  1.4G   1% /dev/shm
none                  1.4G  188K  1.4G   1% /var/run
none                  1.4G     0  1.4G   0% /var/lock
none                  1.4G     0  1.4G   0% /lib/init/rw
[/FONT]

any good?

---

