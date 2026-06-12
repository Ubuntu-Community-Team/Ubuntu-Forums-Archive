---
title: "Nothing mounted on /boot"
date: 2006-06-19
forum: General Help
---

### Post by LeeM on 2006-06-19
:confused: 
A rather newbie to Ubuntu/Linux. I am running dual boot (triple actually) Windoz, Xandros and (mainly) Ubuntu Dapper. I see from several threads that one partition should be mounted on /boot. I don't have that. Here is my df:

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda5              7164704   5824996   1339708  82% /
varrun                  225392       140    225252   1% /var/run
varlock                 225392         4    225388   1% /var/lock
udev                    225392       224    225168   1% /dev
devshm                  225392         0    225392   0% /dev/shm
lrm                     225392     18856    206536   9% /lib/modules/2.6.15-23-386/volatile
/dev/hda1             46082420  30531172  15551248  67% /media/windows
/dev/hda7              4835368   4293528    541840  89% /media/hda7

(Ubuntu on /dev/hda5, Windoz on /dev/hda1, and Xandros on /dev/hda5)..

What should be mounted on /boot?

BTW, I am using GRUB.

Any help would be appreciated!

LeeM

---

### Post by Ramses de Norre on 2006-06-19
Haven't you got just a folder /boot/? Some people prefer to make a seperate partition for this which is mounted at /boot/ then but this isn't really necessary.
I wont bother too much when all is working fine.

---

### Post by tonyr on 2006-06-19
There is nothing mounted on **/boot** by default.  It is simply a directory in
the root filesystem.

If you wanted a separate /boot partition, you would have to have done a little more
work during the **partitioning** stage of the installation, creating other partitions 
and specifying mount points yourself.  

You should look at these tutorials:
[http://www.psychocats.net/ubuntu/partitioning.html]("http://www.psychocats.net/ubuntu/partitioning.html")
[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

---

### Post by LeeM on 2006-06-19
[QUOTE=tonyr]There is nothing mounted on **/boot** by default.  It is simply a directory in
the root filesystem.

If you wanted a separate /boot partition, you would have to have done a little more
work during the **partitioning** stage of the installation, creating other partitions 
and specifying mount points yourself.  

You should look at these tutorials:
[http://www.psychocats.net/ubuntu/partitioning.html]("http://www.psychocats.net/ubuntu/partitioning.html")
[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")[/QUOTE]
 
Thanks! I'll look up the references.

---

