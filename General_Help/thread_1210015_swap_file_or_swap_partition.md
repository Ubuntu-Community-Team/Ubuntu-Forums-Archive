---
title: "swap file or swap partition ??"
date: 2009-07-10
forum: General Help
---

### Post by chinmaya_n on 2009-07-10
Which should i prefer ........... swap file or swap patition ??

Plz help me.!

Thanx:popcorn:

---

### Post by Jebtrix on 2009-07-10
Swap partition is pretty standard in the linux world. Where are you getting a choice?

---

### Post by egalvan on 2009-07-10
I think the file system logic is optimized for a partition.
'swap' is a native *nix partition.

Swap FILES are optimized under Microsoft file ops.

Under *nix, I have never used anything other than a partition.
Many times on it's own drive (in yon olde SCSI-based computyr days :) )
I have never used anything other than a partition.

---

### Post by CatKiller on 2009-07-11
> **chinmaya_n said:**
> Which should i prefer ........... swap file or swap patition ??

It doesn't matter. They both perform about the same. Although I don't know for sure that you can hibernate to a swap file.

---

### Post by chinmaya_n on 2009-07-11
The problem is .......... in my laptop it doesnt allow more than 4 partitions, I 've to keep a swap partition and a /(root) partition.
So i'm left with just 2 partitins in which i've to use one for windows. 
So finally i'll be left with just one partition for my personal data.......!!:(

So if use a swap file than a partition... i could have another partition for my data......;)

> Although I don't know for sure that you can hibernate to a swap file
Does any one know whether we can hibernate using a swap file??

---

### Post by credobyte on 2009-07-11
Might be useful : [http://www.linux.com/archive/feature/113956](http://www.linux.com/archive/feature/113956)

---

### Post by CatKiller on 2009-07-11
> **chinmaya_n said:**
> The problem is .......... in my laptop it doesnt allow more than 4 partitions, 

You can only have four **primary** partitions. You can have as many logical volumes as you want in an **extended** partition. I don't know if it's still the case, but it used to be that Windows would only work if its C: drive was a primary partition, but Linux partitions and data partitions can all happily live in an extended partition.

---

### Post by Ashish Meena on 2009-07-11
check this [http://www.go2linux.org/swap-file-vs-swap-partition](http://www.go2linux.org/swap-file-vs-swap-partition)

See, I believe if you use linux as primary operating system, I would recommend you to use swap partition rather than swap file. If you occasionally login to ubuntu and use windows more than you can go with swap file. however you can always create logical partitions in case of partition problem

---

### Post by chinmaya_n on 2009-07-11
> **CatKiller said:**
> You can only have four **primary** partitions. You can have as many logical volumes as you want in an **extended** partition. I don't know if it's still the case, but it used to be that Windows would only work if its C: drive was a primary partition, but Linux partitions and data partitions can all happily live in an extended partition.

I'll see if u were correct......:p

Does anyone know, is it possible to hibernate with a swap file alone??

---

### Post by chinmaya_n on 2009-09-10
I dont know why this laptop is not allowing to create a logical partition !! 

It is showing all partitions as primary not allowing to create a logical partition during installation!

---

### Post by plucky on 2009-09-10
> **chinmaya_n said:**
> I dont know why this laptop is not allowing to create a logical partition !! 

It is showing all partitions as primary not allowing to create a logical partition during installation!

Post output of ```
sudo fdisk -l
``` That is lowercase L not a 1

Or better still post a screenshot of the partition editor window.

Remember a maximum of 4 primary partitions and the extended partition which contains the logical partitions also counts as a primary partition.


Good Luck

---

