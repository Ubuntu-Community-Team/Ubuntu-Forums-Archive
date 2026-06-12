---
title: "Can I &quot;Expand&quot; a partition???"
date: 2010-03-10
forum: General Help
---

### Post by maghoxfr on 2010-03-10
I have a 300 Gb Hard drive, I used to have windows xp on it but decided to install ubuntu, so what I did (after some suggestions) was to create 3 partitions, one of 30 Gb for windows (I use Adobe software), one of 10 Gb for Ubuntu 9.10 and the rest as a common partition used for storage. Started ok, but I really got hooked with ubuntu and now my partition is full!=D>. My question is ( and here is where I show my deep ignorance and shame): can I "expand" the ubuntu partition gaining space from the storage one? If not, how many Gb would you recommend for an Ubuntu partition? I'm using a lot of music/video/graphics production software. Thanks for any answer, and sorry for the long stupid post.

---

### Post by bluelamp999 on 2010-03-10
I'm pretty sure GParted (Gnome Partition Editor) should fit the bill...

It's not installed by default but it's in Synaptic.

---

### Post by geirha on 2010-03-10
Yes you can, and this will tell you how: [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

If you want some recommendations on wheter you should resize partitions or create new ones, show the output of the following two commands run in a terminal (Applications -> Accessories -> Terminal)
```
df -h
sudo fdisk -l
```

Or show a screenshot of the gparted window.

---

### Post by eriktheblu on 2010-03-10
You certainly can, but not when it's mounted. This means you cannot be running Ubuntu when you resize your Ubuntu partition.

The common answer is to use your Ubuntu live CD and Gparted. I prefer the Gparted live CD as it seems to run faster.

Backup all data before attempting to resize a partition.

For just the programs and no file storage, I like to have about 20GB in my root partition, but you can get away with much less. For my /home partition I use about 150 GB (I also have a couple of other special purpose partitions and quite a bit of unformatted space between partitions)

If you don't have a separate /home partition, [this guide](http://www.psychocats.net/ubuntu/separatehome) is frequently recommended.

---

### Post by maghoxfr on 2010-03-10
```
df -h

S.ficheros            Tamaño Usado  Disp Uso% Montado en
/dev/sda3             7,6G  6,9G  264M  97% /
udev                 1007M  292K 1007M   1% /dev
none                 1007M  2,1M 1005M   1% /dev/shm
none                 1007M  196K 1007M   1% /var/run
none                 1007M     0 1007M   0% /var/lock
none                 1007M     0 1007M   0% /lib/init/rw
/dev/sda6             255G   52G  204G  21% /media/datos

sudo fdisk -l

Disco /dev/sda: 320.1 GB, 320072933376 bytes
255 cabezas, 63 sectores/pista, 38913 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xda32da32

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        3916    31455238+   7  HPFS/NTFS
/dev/sda2            3917        4438     4192965    7  HPFS/NTFS
/dev/sda3            4439        5434     8000370   83  Linux
/dev/sda4            5435       38913   268920067+   5  Extendida
/dev/sda5            5435        5695     2096451   82  Linux swap / Solaris
/dev/sda6            5696       38913   266823553+   7  HPFS/NTFS

```

Thanks for the responses! Another thing I love about Ubuntu: I never get disappointed, even in things that seems impossible, the answer is always yes you can do that. Thanks

---

### Post by maghoxfr on 2010-03-10
oh man I've just realized it's in spanish I'll translate it probably with some wrong terms.

```
df -h

S.folders             Size  Used Availabl Use% Mounted in
/dev/sda3             7,6G  6,9G  264M  97% /
udev                 1007M  292K 1007M   1% /dev
none                 1007M  2,1M 1005M   1% /dev/shm
none                 1007M  196K 1007M   1% /var/run
none                 1007M     0 1007M   0% /var/lock
none                 1007M     0 1007M   0% /lib/init/rw
/dev/sda6             255G   52G  204G  21% /media/datos

sudo fdisk -l


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cilinders
Units = cilinders of 16065 * 512 = 8225280 bytes
Disk identifyer: 0xda32da32

Devicest. Start         End      Blocks  Id  System
/dev/sda1   *           1        3916    31455238+   7  HPFS/NTFS
/dev/sda2            3917        4438     4192965    7  HPFS/NTFS
/dev/sda3            4439        5434     8000370   83  Linux
/dev/sda4            5435       38913   268920067+   5  Extendida
/dev/sda5            5435        5695     2096451   82  Linux swap / Solaris
/dev/sda6            5696       38913   266823553+   7  HPFS/NTFS

```

If somenthig is not clear please tell me.

---

### Post by geirha on 2010-03-10
Ok, you got an 8GB partition for /. That should be sufficient. I recommend you shrink sda6 as much as you feel like, then make a new partition of the freed space, and use that as /home. See the guide eriktheblu posted on how to move /home to the new partition.

---

### Post by maghoxfr on 2010-03-10
Thanks very much that guide looks very complete, I'll read it and tomorrow I'll give it a try. THANKS THANKS THANKS people!!!

---

### Post by geirha on 2010-03-10
> **maghoxfr said:**
> oh man I've just realized it's in spanish I'll translate it probably with some wrong terms.

It didn't matter too much that it was in spanish. The numbers and device names to look for are in the same place regardless of translations.

However, for future reference, you can turn off translations (temporarily) in a terminal by first running export LANG=C:
```
export LANG=C
df -h
sudo fdisk -l

```

or by prepending LANG=C to each command
```
LANG=C df -h
LANG=C sudo fdisk -l
```

---

### Post by maghoxfr on 2010-03-10
Yes I supposed that the important things were numbers, thanks again for that tip, is going to my "dictionary"! Tomorrow night i'll post to tell if i did it or not

---

