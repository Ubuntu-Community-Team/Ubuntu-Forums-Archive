---
title: "Partitioning Question"
date: 2009-07-08
forum: General Help
---

### Post by theidkman on 2009-07-08
Alright, so I want to make my ubuntu partition somewhat bigger. The problem is, I don't know how ot do that without damaging my Windows Vista partition. I would like to know how to just decrease the size of my Windows Vista partition, then use that extra space for my ubuntu partition.

---

### Post by wojox on 2009-07-08
Hey theidkman,

Boot from live cd and run the gparted.

---

### Post by merlinus on 2009-07-08
No, no, no!  Use vista's disk management tool to shrink its partition, and defrag several times first.  If you use gparted you run the risk of damaging vista and losing data.

A search on the forum will bring up any number of threads about this happening.

gparted works fine with xp and 2000, but definitely not with vista.

OTOH, it may work fine for you....

---

### Post by theidkman on 2009-07-09
> **merlinus said:**
> No, no, no!  Use vista's disk management tool to shrink its partition, and defrag several times first.  If you use gparted you run the risk of damaging vista and losing data.

A search on the forum will bring up any number of threads about this happening.

gparted works fine with xp and 2000, but definitely not with vista.

OTOH, it may work fine for you....

I shrunk my Windows Vista partition a good amount(~4GB). I tried to extend the ubuntu partition, but when I right-click on that volume, it doesn't allow me to extend it. It only allows me to delete it, and check the properties.

---

### Post by merlinus on 2009-07-09
Post results of 

```
sudo fdisk -l
```

and if possible, a screenshot of gparted.

---

### Post by theidkman on 2009-07-09
> **merlinus said:**
> Post results of 

```
sudo fdisk -l
```

and if possible, a screenshot of gparted.

```
ub3rn00b3rs@ub3rn00b3rs-laptop:~$ sudo fdisk -l
[sudo] password for ub3rn00b3rs: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x89f2d762

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19018   152758120    7  HPFS/NTFS
/dev/sda2           19551       28985    75786637+   5  Extended
/dev/sda3           28986       30402    11373568    7  HPFS/NTFS
/dev/sda5           19551       28595    72653931   83  Linux
/dev/sda6           28596       28985     3132643+  82  Linux swap / Solaris
```

---

### Post by sdlynx on 2009-07-09
> **merlinus said:**
> No, no, no!  Use vista's disk management tool to shrink its partition, and defrag several times first.  If you use gparted you run the risk of damaging vista and losing data.

A search on the forum will bring up any number of threads about this happening.

gparted works fine with xp and 2000, but definitely not with vista.

OTOH, it may work fine for you....

I did the on the other hand blindly lol... lucky for me it worked.
+1 for this though

---

### Post by beaver_07 on 2009-07-09
Hi,
on our machine there're two HDD's; 250GB and 200GB (C:/, D:/)
To shrink and expand existent partitons wasn't and is of no good, by any means.
When it comes to altering existent partions, it starts with part 1, 2 and 3.
When Windows was installed first, XP/Vista is on partition 1. Linux's SWAP
partiton normally is partiton 2, the 3rd partiton is Linux itself.
When you want to alter the size of 1 or 3 (Vista shrinking and Linux expanding),
it will take you some time to do this according to the volume of data on both partitons.
Under Windows goto MyComputer, right-click C:/ (the HDD you want to with) and do DEFRAG. After defragmentation the data in the Windows partiton are alligned and remaining space can be used to expand the Linux partiton and here it comes;

traditionally between the 1st (Windows) and 3rd (Linux) partiton is the 2nd, Linux's SWAP partiton. SWAP is the same what page file is under Windows and serves as unformatted part on the HDD to transfer any RAM data on HDD before the machine turns off.
When you shrink Vista partiton, no problem, but to also expand Linux means you shift the SWAP partiton up all the way right after the Windows partiton. All data on the Linux partiton will be copied and relocated while the partiton expands until finally the partiton reached the intended size and is in a sober way defragmented.
Although I delightfully confirm under Linux it won't take that long.
Try to format a partiton under Linux and then try to do under Windows: 110GB under Ubuntu is less than 10 sec. under XP it's 30 min. I went through, was there.

Suggestion is to get all your data on file (CD's,DVD's) and decide how much volume you want to allocate for each OS before installing each of them side by side. 
Hint: you might have heard during linux installation that you can have direct access onto XP's/Vista's MyDoc,  MyMusic,  MyVideos and meantime even myComputer from the Linux partition under Linux.

---

### Post by merlinus on 2009-07-09
You will first need to resize the extended partition, sda2, and then sda5.

---

### Post by theidkman on 2009-07-09
Alright, so I thank all of you for the answers. I figured it out, and got it to work by using gparted. It did not damage my Vista partition. 

Although I got it to work, what I decided to do afterwards was to just transfer my important data that I "absolutely" needed(music) onto my external HDD. Then I just reinstalled ubuntu partitioning the entire drive for it. The only reason I needed Vista was because of my Zune. So now I'm just using a VM to get my music to, and from my Zune. 

So thank you all for the answers.

---

### Post by mavis311 on 2009-07-18
> **merlinus said:**
> No, no, no!  Use vista's disk management tool to shrink its partition, and defrag several times first.  If you use gparted you run the risk of damaging vista and losing data.

A search on the forum will bring up any number of threads about this happening.

gparted works fine with xp and 2000, but definitely not with vista.

OTOH, it may work fine for you....


I just installed ubuntu on my laptop with Vista and I have similar issues.  I wanted to change the size of my ubuntu root and swap partitions, but both gparted and Vista's disk management show the same thing:  There is no actual partition for unbuntu.  Further investigation reveals that my ubuntu install (installed via wubi) is in C:\ubuntu.

My HDD has two partitions: 1) recovery partition 1.46 GB, 2) Vista partition 184.84 GB.  I selected a 16 GB ubuntu partition at install and the ubuntu folder makes up that much HDD space under Vista.

EDIT:
Disregard this.  I have a much greater understanding of wubi.

---

