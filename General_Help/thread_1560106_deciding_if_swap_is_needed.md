---
title: "deciding if swap is needed"
date: 2010-08-24
forum: General Help
---

### Post by bathacid on 2010-08-24
If i have 6GB of phy ram some one told me that swap was not needed was just wanting to make sure before i partitioned it. and if it is not needed how can i make the swap partition add to my root partition or will it automatically do that once i make it ext4 since it is the only partition like that

---

### Post by quizno50 on 2010-08-24
If you have 6GB of ram you shouldn't need swap space. When you install ubuntu just make sure you partition manually and don't add the swap partition just allocate all your hard drive for the / partition. Also, if you decide later you want swap space on your system, you can add it by making a swap file (just google around for some instructions, or look at the manpage for mkswap).

---

### Post by Onesimus on 2010-08-24
My understanding is that if you want to hibernate your machine your need to create a swap partition.  This needs to be twice the size of your ram.

---

### Post by bathacid on 2010-08-24
well i already have ubuntu installed it is my only os on this laptop is there a way that i can just make it alot smaller its 8GB atm because of the guided partiton when i set up ubuntu

---

### Post by WorMzy on 2010-08-24
Dude, commas. Use them. They're not your enemy.

I'd say you don't need a swap partition. If you decide to add one later on, then you just need to make an entry for it in /etc/fstab.

The entry should look something like this:
```
UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx swap swap defaults 0 0
```

---

### Post by QLee on 2010-08-24
bathacid,

If you want to be able to hibernate your system you need a swap of sufficient size to hold the contents of RAM. If you choose to not hibernate, with 6 GB of RAM, you'd likely not hit swap anyway unless you're doing some memory intensive tasks.

---

