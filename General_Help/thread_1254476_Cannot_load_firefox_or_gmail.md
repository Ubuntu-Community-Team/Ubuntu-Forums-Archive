---
title: "Cannot load firefox or gmail"
date: 2009-08-31
forum: General Help
---

### Post by lakelovers on 2009-08-31
Something is wacko with the sda1 drive or partition. I installed and formated a USB drive for backups, only. I went though hoops trying to partition the drive with the help of this forum. I finally reverted to a single partition sdb1. When I booted the computer this morning, I could not launch Firefox or download emails from gmail, What do you suppose is going on? I'm writing this on Konqueror which is working as it should.

I'm getting messages that my primary drive is full. I had over 50% of the drive unused before I started messing with the USB drive. When I go to gparted, it does indeed show all but a tiny bit used. What's going on? How do I repair this?

---

### Post by lakelovers on 2009-08-31
I need help before I panic. The reason I can't load firefox of get my gmail is because the error message says my hard drive is full, but I can't find any huge files that would contribute to an overload on the 80GB drive (admittedly not large). I see on gparted that fall files/folders have gone into /dev/sda1 (73 GB). SDA2 has only 1.43 GB. I don't suppose it makes any difference but I thought that sda1 is suppose to hold only the system files.. I guess I have to start deleting folders/files. I open to any suggestions on how to solve this problem

---

### Post by credobyte on 2009-08-31
```
sudo du -h --max-depth=1 / 
```

Can you post the output ?

---

### Post by lakelovers on 2009-08-31
4.0K	/selinux
2.2G	/lost+found
747M	/lib
7.5M	/sbin
0	/sys
29G	/var
du: cannot access `/proc/8152/task/8152/fd/3': No such file or directory
du: cannot access `/proc/8152/task/8152/fdinfo/3': No such file or directory
du: cannot access `/proc/8152/fd/3': No such file or directory
du: cannot access `/proc/8152/fdinfo/3': No such file or directory
0	/proc
40M	/root
6.1M	/bin
du: cannot access `/home/jerry/.gvfs': Permission denied
6.9G	/home
4.8G	/usr
4.0K	/initrd
4.0K	/mnt
992K	/tmp
1.1M	/media
20M	/etc
87M	/opt
4.0K	/srv
236K	/dev
96M	/boot
44G	/

---

### Post by credobyte on 2009-08-31
Ehh, forgot to add this one:
```
df -h
```

It'll list all partitions and their size / used space.

---

### Post by lakelovers on 2009-08-31
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              72G   71G     0 100% /
tmpfs                 501M     0  501M   0% /lib/init/rw
varrun                501M  220K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M  148K  501M   1% /dev
tmpfs                 501M   88K  501M   1% /dev/shm
lrm                   501M  2.2M  499M   1% /lib/modules/2.6.28-15-generic/volatile
/dev/sdb1             114G   75M  108G   1% /media/sdb1
overflow              1.0M 1008K   16K  99% /tmp

---

### Post by credobyte on 2009-08-31
> **lakelovers said:**
> Filesystem            Size  Used Avail Use% Mounted on
**/dev/sda1              72G   71G     0 [COLOR=Red]100%[/COLOR] /**
tmpfs                 501M     0  501M   0% /lib/init/rw
varrun                501M  220K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M  148K  501M   1% /dev
tmpfs                 501M   88K  501M   1% /dev/shm
lrm                   501M  2.2M  499M   1% /lib/modules/2.6.28-15-generic/volatile
/dev/sdb1             114G   75M  108G   1% /media/sdb1
overflow              1.0M 1008K   16K  99% /tmp

It's full! 

Does this end up with something useful ( files found ) ?
```
find / -size +1G -exec ls -l {} \;
```

---

### Post by lakelovers on 2009-08-31
That gave me a very long list all of which permission was declined. So I did a sudo and got this

-rw-r----- 1 root admin 2039578624 2008-05-19 21:07 /lost+found/2008-05-19_20.37.59.519720.jerry-desktop.ful/files.tgz
-rw------- 1 root root 5488838296 2009-08-29 06:24 /var/archives/jerry-desktop-home-jerry.20090829.master.tar.gz
-rw------- 1 root root 5478292489 2009-08-27 12:56 /var/archives/jerry-desktop-home-jerry.20090827.master.tar.gz
-rw------- 1 root root 5497105212 2009-08-30 08:29 /var/archives/jerry-desktop-home-jerry.20090830.master.tar.gz
-rw------- 1 root root 5472915722 2009-08-28 11:32 /var/archives/jerry-desktop-home-jerry.20090828.master.tar.gz
-rw------- 1 root root 5472869051 2009-08-31 06:38 /var/archives/jerry-desktop-home-jerry.20090831.master.tar.gz
-rw-r----- 1 root admin 2114349862 2008-05-04 21:33 /var/backup/2008-05-04_21.13.22.552395.jerry-desktop.ful/files.tgz
find: `/proc/10931/task/10931/fd/5': No such file or directory
find: `/proc/10931/task/10931/fdinfo/5': No such file or directory
find: `/proc/10931/fd/5': No such file or directory
find: `/proc/10931/fdinfo/5': No such file or directory
-rw------- 1 jerry jerry 1663050240 2009-06-19 17:16 /home/jerry/.VirtualBox/VDI/virtualHardDisk1.vdi
find: `/home/jerry/.gvfs': Permission denied


 I tried deleting files, but I can't delete anything. I tried this using rm command in the terminal. I also tried moving stuff to trash but that didn't work either. How can I delete files when the drive is full?. BTW, thank you for your help. Sometimes computers get very frustrating when I don't know what I'm doing. . . which is most of the time.. It's interesting that I just bought a 120GB drive for backups when I should have been thinking about the main drive. If I had realized that the drive was so short on space, I would have deleted files long before this happened. I always monitored the available storage capacity but I must have been watch the wrong numbers.

Can I copy files from the sda to the sdb drive? I'll try but I have an idea if I can delete files I probably can copy either.

Will it help if I give you the total list of the output from "find / -size +1G -exec ls -l {} \; ?"

---

### Post by credobyte on 2009-08-31
```
sudo rm -r /home/jerry/.VirtualBox/VDI/virtualHardDisk1.vdi
```
[COLOR=Red]**WARNING!**[/COLOR] It will delete one of your VirtualBox hdd images - choice is up to you ..

This should give you a few gigs of space .. if not, try to move them ( just a temporary solution ).
```
sudo mv /home/jerry/.VirtualBox/VDI/virtualHardDisk1.vdi /media/sdb1
```

---

### Post by lakelovers on 2009-08-31
Okay, I'll do that and let you know the outcome. Also, could I delete the linux swap partition?

---

### Post by lakelovers on 2009-08-31
The first command gave me 3.39 GB.

---

