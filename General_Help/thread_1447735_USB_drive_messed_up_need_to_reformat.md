---
title: "USB drive messed up: need to reformat"
date: 2010-04-05
forum: General Help
---

### Post by elaliberte on 2010-04-05
Hi, I have a 16-GB USB drive that I want to reformat. It's really messed up.

when I type

```
sudo fdisk -l 
```it tells me that /dev/sdb only has 8111 mb. And Gparted only shows my an unallocated 7.55 gb drive. I don't understand anything. I just want my USB drive to be fully reformatted and work again!

Any help would be much appreciated.

---

### Post by Revolutionary101 on 2010-04-05
Open Gparted to take the already existing partition and resize it. 

Just right click on the partition that already exists and click "resize/move". When the new window opens just increase the "New Size" number up to the maximum. Then just click on the green check mark on the top of the window, to apply the changes.

---

### Post by elaliberte on 2010-04-05
Thanks. Looks like I have no partition on the drive. So I tried to create one but Gparted returns this error (translated from French so choice of words may not be right):

Create primary partition #1 (fat32, 7.55 gb) on /dev/sdb
Create an empty partition
path: /dev/sdb1
start: 0
end: 15840089
size: 15840090 (7.55 gb)

messages from libparted:
unable to open /dev/sdb - disk label not recognized

---

### Post by elaliberte on 2010-04-05
Ok sorry, I have tried without including a label and it worked. BUT there's obviously something wrong. It tells me that the maximum size is 7734 mb. However, I know that I have twice that capacity (16 gb). Why can't I see the full storage capacity? Gparted used to tell me its storage was 15.1 gb or so... I don't understand.

Thanks

---

### Post by elaliberte on 2010-04-05
Is it possible that the drive itself is damaged, preventing me to have access to its formal full capacity?

Here's what sudo fdisk -l gives me, sorry for french

```

etienne@globetrotter:~$ sudo fdisk -l

Disque /dev/sda: 100.0 Go, 100030242816 octets
255 têtes, 63 secteurs/piste, 12161 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets
Identifiant de disque : 0x08000000

Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sda1   *           1       11661    93666951   83  Linux
/dev/sda2           11662       12161     4016250    5  Etendue
/dev/sda5           11662       12161     4016218+  82  Linux swap / Solaris

Disque /dev/sdb: 8111 Mo, 8111783936 octets
255 têtes, 63 secteurs/piste, 986 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets
Identifiant de disque : 0x000b76cf

Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sdb1               1         986     7920013+   b  W95 FAT32
etienne@globetrotter:~$ ^C
etienne@globetrotter:~$ 


```

---

### Post by Revolutionary101 on 2010-04-05
I am glad that you can it partitioned correctly. It looks that it might have been damaged and that may be why you are only seeing 8 GB. I don't know of any other way why it would only be detecting 8 GB.

---

### Post by garvinrick4 on 2010-04-05
In gparted what does it say for used space? Every time I get one screwed up the only
place I could get them back in order was in gparted.

---

### Post by elaliberte on 2010-04-05
gparted tells me it has 7.5 gb (7734 mb is the max it allows me for a partition to be exact).

I tried

```
sudo dd if=/dev/zero of=/dev/sdb bs=16065b
```

to get rid of all data, which was successful. I also deleted all partitions on /dev/sdb. However, still only 7.5 gb.

Running
```
sudo fdisk -l
```

still gives me the same info as previously posted, i.e. that /dev/sdb has 8111 mb...

So is all hope lost, and should I conclude that the disk has been damaged/corrupted?

Thanks

---

### Post by elaliberte on 2010-10-15
The problem was that my disk was corrupted. Oh well.

---

