---
title: "I'm trying get updates from update manager"
date: 2010-05-07
forum: General Help
---

### Post by Skipopis on 2010-05-07
I'll explain again: I'm trying get updates from update manager and it says "the upgrade needs a total of 498M free space on disk '/'. Please free at least an additional 495M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'." I ran sudo apt-get clean n it did nothing. please help

---

### Post by lmarmisa on 2010-05-07
Open a terminal an type this command:

> 
df -h
Tou will get an answer similar to this:

> 
lmarmisa@UBUNTU910ENG:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              14G  3.4G  9.2G  27% /
udev                  249M  228K  249M   1% /dev
none                  249M  864K  248M   1% /dev/shm
none                  249M  312K  249M   1% /var/run
none                  249M     0  249M   0% /var/lock
none                  249M     0  249M   0% /lib/init/rw
none                   14G  3.4G  9.2G  27% /var/lib/ureadahead/debugfs
share                 466G  374G   92G  81% /media/share
lmarmisa@UBUNTU910ENG:~$ 
Check the space available in your / partition (in my case is 9.2 Gbytes).

Best regards,

Luis

---

### Post by Skipopis on 2010-05-07
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             2.3G  2.2G   96K 100% /
tmpfs                1003M     0 1003M   0% /lib/init/rw
varrun               1003M  104K 1003M   1% /var/run
varlock              1003M     0 1003M   0% /var/lock
udev                 1003M  148K 1003M   1% /dev
tmpfs                1003M   84K 1003M   1% /dev/shm
lrm                  1003M  2.4M 1000M   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M   12K 1012K   2% /tmp

And

---

### Post by lmarmisa on 2010-05-07
You have no free space in your / partition. You would need a greater partition for your Ubuntu system.

Best regards,

Luis

---

### Post by Skipopis on 2010-05-07
And how would I make my partition bigger. please n thanx

---

### Post by lmarmisa on 2010-05-07
Your partition is full. 2.3 Gbytes is too small for your Ubuntu system. There are several solutions for your problem (if you have free space in your HDD, of course) , but they are not trivial.

Type this command in order to evaluate the possibility to expand, move or add other partitions to your system:

> 
fdisk -l


Regards,

Luis

---

### Post by sr_guy on 2010-05-07
Get a bigger harddrive

---

### Post by Skipopis on 2010-05-07
typed in fdisk -l nothing happened

---

### Post by lmarmisa on 2010-05-07
Sorry, I forgot the sudo prefix:

```

sudo fdisk -l

```

---

### Post by Skipopis on 2010-05-07
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfab9fab9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29653   238187691   83  Linux
/dev/sda2           29654       30401     6008310    5  Extended
/dev/sda5           29654       30075     3389683+  82  Linux swap / Solaris
/dev/sda6           30076       30379     2441848+  83  Linux
/dev/sda7           30380       30401      176683+  82  Linux swap / Solaris

---

### Post by lmarmisa on 2010-05-07
It seems that you have two Linux installations in your system. Is it right?.

Compare the huge Linux partition /dev/sda1 of 238 Gbytes with the tiny Ubuntu partition /dev/sda6 of only 2.4 Gbytes. This is the problem.

Could you tell me a little more about the installations that you have defined in your system?.

Luis

---

### Post by cuberts on 2010-05-07
> **Skipopis said:**
> And how would I make my partition bigger. please n thanxIt is very hard to change your partition, so I recommend that you reinstall your Ubuntu, and then when you are reinstalling it then you can reset the partition.

---

### Post by lmarmisa on 2010-05-07
A re-installation of Ubuntu is not the solution because there is no free space enough in the hard drive.

He should reinstall the two Linux systems, defining appropriately the sizes of the different partitions.

---

### Post by Skipopis on 2010-05-08
I dont want two linux operating systems I want the newest one How do I know the difference and how do I get rid of the one I don't want. Please n thanx

---

