---
title: "running out of inodes"
date: 2010-11-13
forum: General Help
---

### Post by asus701user on 2010-11-13
I think I am running out of inodes on my eeepc701. It has happened before when I was using Xandros but now I am using Ubuntu 10.04.

I get the following output:

df -i
Filesystem            Inodes   IUsed   IFree IUse% Mounted on
/dev/sda1             230144  213725   16419   93% /
none                   61531     765   60766    2% /dev
none                   62587       5   62582    1% /dev/shm
none                   62587      70   62517    1% /var/run
none                   62587       1   62586    1% /var/lock
none                   62587       3   62584    1% /lib/init/rw
/dev/sdb1                  0       0       0    -  /media/ALAN

df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             3.5G  3.1G  250M  93% /
none                  241M  292K  241M   1% /dev
none                  245M  164K  245M   1% /dev/shm
none                  245M  528K  244M   1% /var/run
none                  245M     0  245M   0% /var/lock
none                  245M     0  245M   0% /lib/init/rw
/dev/sdb1              30M  279K   30M   1% /media/ALAN[FONT=Verdana]

[/FONT][FONT=Verdana]The number of inodes has been going down over several months and I think that 
running Update Manager does not help. There seem to be very many small files 
(like tty to ttyS3) in dev and its subdirectories and all the files seem to have todays date.

When using Xandros the following worked to free up the inodes:
[/FONT]
$ su
[enter password at prompt]
# mkdir -pv /mnt/sda2
# mount /dev/sda2 /mnt/sda2
# find /mnt/sda2 -iname '.wh*' -delete
[wait a long-ish while, then check your new IFree count:]
# df -i
[don't forget to clean up:]
# umount /dev/sda2
# exit

[FONT=Verdana]Will that work with Ubuntu? And do I use sda1 rather than sda2? 
I don't seem to have an sda2 now (or I can't see it).


Many thanks




[/FONT]

---

