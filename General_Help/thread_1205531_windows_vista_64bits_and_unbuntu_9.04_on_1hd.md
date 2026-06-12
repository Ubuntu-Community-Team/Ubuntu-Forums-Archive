---
title: "windows vista 64bits and unbuntu 9.04 on 1hd"
date: 2009-07-06
forum: General Help
---

### Post by leonbuntu on 2009-07-06
dear all,
 
can some1 pls help me.
 
i am new to ubuntu.
 
i have a 160gb sata hd. vista 64bits is already installed on it. and only 25gb used.
 
i have just installed ubuntu onto this sata hd. all working fine, i can select which os i want.
 
problem is, i cannot use ubuntu, whenever i use the add/remove option in ubuntu to add compiz download, it say not enough space, looks like ubuntu set the partition limited, how can i make the ubuntu partition to 30gb, instead of 2gb, it was auto partition.
 
i have also reinstalled vista 64bit and then ubuntu, to run on top, but till the same.
 
i am new to linux, so pls try to make it easy :lolflag:
thx.

---

### Post by earthpigg on 2009-07-06
can you show us the output of this, please:

```
df -h
```

---

### Post by leonbuntu on 2009-07-06
ok, i will add the output tonight when i get home, thx.

---

### Post by leonbuntu on 2009-07-06
this is the detail i got from running your command you gave me.

[B]Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.3G     0 100% /
tmpfs                 3.6G     0  3.6G   0% /lib/init/rw
varrun                3.6G  108K  3.6G   1% /var/run
varlock               3.6G     0  3.6G   0% /var/lock
udev                  3.6G  156K  3.6G   1% /dev
tmpfs                 3.6G  496K  3.6G   1% /dev/shm
lrm                   3.6G  2.7M  3.6G   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M   16K 1008K   2% /tmp
leon@leon-desktop:~$ [/B]

i have no clue what they mean.

my hd is sata 160gb.

i installed vista 64bit on it full.
then i installed ubuntu 9.94, but it auto set my partition, i wish to have 30gb for ubuntu 9.04 and the rest for vista 64bit.

how can i repartition ubuntu? i can reinstalled it, but i dont want to reinstall vista again. unless i must.

here is another message if i try to add a application:

[B]E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/B]

thx.

---

### Post by earthpigg on 2009-07-07
to resize your existing partitions, boot from the ubuntu live cd, open a terminal and type in 'gparted' to start the partition editor.

as always when doing anything involving partitions, ensure you have a solid backup of all your stuff both in windows and in ubuntu before doing this.

---

### Post by ngsupb on 2009-07-07
earthpigg is right. Just add more space to the Ubuntu's partition by using gparted from the live cd

---

### Post by leonbuntu on 2009-07-07
okie, i will try later and let you know how it goes, thxxx.
 
i have all my data on a external hd as always, so my c drive or ubuntu is a hd for programs and os only.
 
 
anothers question, my keyboard is german and set as german default, but how come i cant use the "at" symbol? in germany we always use cntrl+alt+Q, with vista i can, but not in ubuntu? so i had to go to some website copy and paste the symbol all time :lolflag:

---

### Post by leonbuntu on 2009-07-08
i ve tried the gparted but i dont think it work, i dont have the live cd, i downloaded ubuntu from the website. i even tried to started it in the terminal when i am in ubuntu.
 
then i decided to reinstall ubuntu from the dvd again, and i repartition it manually (after figuring how to) now i have 30gb on ubuntu :-D
 
thanks for your support.

---

