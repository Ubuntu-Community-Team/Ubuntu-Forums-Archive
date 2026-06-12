---
title: "What happend to my Ubuntu?!?!"
date: 2009-08-24
forum: General Help
---

### Post by mac666 on 2009-08-24
Hey
Yesterday i rebooted my computer and after that it was never the same;
My Evolution account was removed
Emererald has to be activated with "emerald --replace"
Compiz do work (it didnt work at first)
Gnome-do wont summon
My firefox bookmarks was gone 2-3 reboots (now here)
My places bookmarks is still gone
I have to activate the best quality in "Apperence" everytime i boot

All after getting a weird message about to little space on the HDD.
I do have space now?


EDIT: Now my shortcuts is gone too!!! :|

---

### Post by P4man on 2009-08-24
sounds like harddisk is too full. If you run ubuntu for a while, it will probably fill to the point where you get in trouble, and after a reboot,it may just work again.. for a bit. When your root partition is full, expect all kinds of weirdness.

You'll have to make space or grow your partition.

At least, assuming your / is indeed full.

---

### Post by exutable on 2009-08-24
Yeah,

A few days ago I accidentally filled up my home partition and weird things started happening involving it, like when I tried to seed torrents they would just keep rechecking and scripts stored in my home directory wouldn't always work etc.

---

### Post by mac666 on 2009-08-24
Argh!!!
i cannot find any files filling my 5GB ubuntu drive....
Im using disc using analizer or what its called in english
But cannot see to get up to 5GB... (exept my windows drive who has 7GB free space...

---

### Post by wojox on 2009-08-24
Try this thread and see if it helps:

[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

---

### Post by P4man on 2009-08-24
5GB is really small for ubuntu.
You can maybe get some temporarily relief by typing:

```
sudo apt-get autoremove
sudo apt-get clean
```

that will delete cached and unused packages.

To analyze your harddisk, run:

```
baobab
```

(then scan your filesystem)

But again, 5GB.. really doesn't cut it for long.

---

### Post by mac666 on 2009-08-24
Can i give my ubuntu partition extra space somehow?

---

### Post by P4man on 2009-08-24
yeah, you can resize your partitions. But then you'll need free space elsewhere. Boot from a live cd, and run partition editor to resize / move delete your partitions. How big is your drive ?

---

### Post by mac666 on 2009-08-24
its only 300 gb..
ive ordered an 1TB drive that should come anyday... Could i "move" my ubuntu to this drive?

---

### Post by P4man on 2009-08-24
yes, with some hackery you can transfer your current installation to the new drive. However, 300GB isn't *that* small. Surely you must have some space somewhere to grow your ubuntu partition beyond 5GB ?

Can you post the output of 

```
sudo fdisk -l
```

---

### Post by mac666 on 2009-08-24
Disk /dev/sda: 320,0 GB, 320072933376 byte
255 huvuden, 63 sektorer/spår, 38913 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte
Diskidentifierare: 0xfce66c60

    Enhet Start     Början        Slut     Block    Id  System
/dev/sda1   *           1       37806   303675671    7  HPFS/NTFS
/dev/sda2           37807       38913     8891977+   5  Utökad
/dev/sda5           37807       38859     8458191   83  Linux
/dev/sda6           38860       38913      433723+  82  Linux växling / Solaris

---

### Post by P4man on 2009-08-24
If you are booting from the live cd, do me a favor next time and select english as language :) Or french, german, dutch.. :D

I guess "Utökad " means Extended? and växling is swap ?

Anyway, if you got enough free space on that windows drive, we can shrink that and resize the others. If you want to wait for your new drive, we can try moving your install there instead. let me know what you want to try.

---

### Post by mac666 on 2009-08-24
I guess i will keep the installation at the 320 gb drive, and move some other stuff...
And your Swedish / English translation was excelent :)..
How ever,
how can i get back the lost shortcuts, et c?

---

### Post by mac666 on 2009-08-24
Codec is allso removed... WTF is this?!

---

