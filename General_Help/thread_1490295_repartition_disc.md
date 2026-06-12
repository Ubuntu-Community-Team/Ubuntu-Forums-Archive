---
title: "repartition disc"
date: 2010-05-22
forum: General Help
---

### Post by guyholmes on 2010-05-22
Hi,
I have ubuntu 9.04 and I want to upgrade to 9.10 but I can't, as when I try, I get the message that there is not enough space. Here is the terminal readout:
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              17G   15G  2.0G  88% /
tmpfs                 431M     0  431M   0% /lib/init/rw
varrun                431M  240K  431M   1% /var/run
varlock               431M     0  431M   0% /var/lock
udev                  431M  152K  431M   1% /dev
tmpfs                 431M   84K  431M   1% /dev/shm
lrm                   431M  2.5M  429M   1% /lib/modules/2.6.28-18-generic/volatile
/dev/sda1              20G   16G  3.7G  82% /media/hda1
/dev/sda5             196G  115G   81G  59% /media/hda5
It seems I need to repartition the disc, but when I try to open the FDE partition manager I get the following readout in the terminal:
guy@linuxpc:~$ sudo partitionmanager
[sudo] password for guy: 
Error: "/var/tmp/kdecache-guy" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-guy" is owned by uid 1000 instead of uid 0.
I'm not very computer literate, so could you guide me through the process of repartitioning the disc? I'd like to take space from hda5 and allocate some to hda1 (Windows) and some to the Linux part of the disc.
Thanks,

Guy

---

### Post by guyholmes on 2010-05-25
I have managed to upgrade without having to repatition after all.

---

