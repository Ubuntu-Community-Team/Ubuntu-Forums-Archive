---
title: "list HD contents"
date: 2009-11-23
forum: General Help
---

### Post by intimatewipe on 2009-11-23
hello Peeps,
            Can this be done,I have several HD's from 500g to 750g mostly in NTFS-3g(3.1) that are fully loaded,I want to list all folders/sub folders and files and then print them out as a reference(because these drives are only occasionally attached by esata/usb)while I have been using linux for a few years  I am only now learning how incredibly handy the terminal is,I know(believe) every drive has a root dir and maybe if I can cd into this can I use the ls -al command to create a text file that I can print off.For eg.Using df I get the following


kris@kris-desktop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb1            151628736  25504160 118422216  18% /
tmpfs                  1030420         0   1030420   0% /lib/init/rw
varrun                 1030420       116   1030304   1% /var/run
varlock                1030420         0   1030420   0% /var/lock
udev                   1030420       200   1030220   1% /dev
tmpfs                  1030420     18324   1012096   2% /dev/shm
lrm                    1030420      2192   1028228   1% /lib/modules/2.6.28-16-generic/volatile
/dev/sda2            894836564 878562064  16274500  99% /media/New Volume
/dev/sdc5             68715516  15323020  53392496  23% /media/disk
/dev/sdc2            902459400 749320284 153139116  84% /media/New Volume_
/dev/sda5             74334908   2821564  67737268   4% /media/disk-1
/dev/sdd2              1862560    949216    913344  51% /media/TITTYBUTLEC
kris@kris-desktop:~$ 
I can see that sdc5/sdc2 are a disk I would like to target,sdc5 is a bootable windows partition(you never know when you might need one)which I can ignore but how can I print out sdc2 as described above,presently it is usb'd but I have an externel sata I can  use.Please be patient with me as I normally use my linuxBox for everyday stuff which it does extremely well and I have enjoyed very much two years of virus/trojan free
computing but I am not a power user and my skills are scratchy but improving:).
While I'm here I would like to thank the kind individuals who helped me get my first ubuntu box up and running two years ago and to all the peeps who write excellent howtos etc for us perpetually bewildered,for my part I have helped two friends with Vista ready laptops (that where not) see that it was not their hardware;) and 3 more that use linux in VMware as 
a taster(just a matter of time).
thanks in advance
Kris

---

### Post by oldos2er on 2009-11-23
Mount the partition, e.g. /dev/sdc5 on /media/disk. Then in a terminal, run **cd /media/disk** then **ls -laR > ~/disk.contents**

 You can then print the file disk.contents.

---

### Post by intimatewipe on 2009-11-23
Thanks OLDos2er,

            Will give it a go,sounds right,should have been mounting.
Thanks again:D

---

### Post by intimatewipe on 2009-11-23
Hi,
This does work but only with ext3 partitions,no joy with ntfs,it would have a different root directory as a windows disk,all the disks are mounted and using umount to try and swap them does not fly,might have to fire up windows but I hate admitting defeat:shock:
it is certainly do-able but I have googled adfinitum and lots of clever stuff shows up but not this.Must remember ntfs is no VIP in linux land,why should it read ntfs,be like asking a Frenchman to speak English in Calais,why should he:-#

---

### Post by intimatewipe on 2009-11-23
Hi,
This does work but only with ext3 partitions,no joy with ntfs,it would have a different root directory as a windows disk,all the disks are mounted and using umount to try and swap them does not fly,might have to fire up windows but I hate admitting defeat:shock:
it is certainly do-able but I have googled adfinitum and lots of clever stuff shows up but not this.Must remember ntfs is no VIP in linux land,why should it read ntfs,be like asking a Frenchman to speak English in Calais,why should he:-#
ooops got distracted by some stuff on the tv,

---

### Post by Spectre5 on 2009-11-23
> **intimatewipe said:**
> Hi,
This does work but only with ext3 partitions,no joy with ntfs,it would have a different root directory as a windows disk,all the disks are mounted and using umount to try and swap them does not fly,might have to fire up windows but I hate admitting defeat:shock:
it is certainly do-able but I have googled adfinitum and lots of clever stuff shows up but not this.Must remember ntfs is no VIP in linux land,why should it read ntfs,be like asking a Frenchman to speak English in Calais,why should he:-#
ooops got distracted by some stuff on the tv,

For NTFS, you need ntfs-3g, see [https://help.ubuntu.com/community/MountingWindowsPartitions/](https://help.ubuntu.com/community/MountingWindowsPartitions/)

---

### Post by intimatewipe on 2009-11-23
Thank you Spectre5,
                   Bang on the button,there is a very similar thread running at the mo and he used ntfs-3g as you say and bingo,I have asked in his thread but if you know how can I list all folders and sub folders and files ,If i use ls -al I get the main folders only,I tried using the other eg above but it did not work,thanks again:D

---

### Post by intimatewipe on 2009-11-23
Can't believe I did not find that Spectre5,just what I was looking for
:guitar:

thankyou-repeat*1000

---

### Post by Spectre5 on 2009-11-23
Glad this solved the problem.  As mentioned before by oldos2er, "ls -laR" should work.  It will print EVERYTHING in the directory it is run in and below (include hidden files and folders).  Copy the command, it is all letters, so ell the letter, not one.

If you included oldos2er's whole command, then it included sending the command output to a file, not to the screen (so you wouldn't see the contents on the screen).  Instead you would find it in a file called disk.contents in your home (~ is for home) folder.

---

