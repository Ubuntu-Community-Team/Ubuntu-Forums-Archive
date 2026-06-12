---
title: "What to format my External Hard Drive"
date: 2009-08-12
forum: General Help
---

### Post by razorboy5 on 2009-08-12
Hi

I have a new External Hard Drive
so as i understand it Ubuntu uses ext3 and windows uses NFTS
i need my external to work on both Ubuntu and Windows since my brother uses Vista

what's the "best" format for that purpose?
read alot of people use FAT32 but is that good for my use?

thx

---

### Post by Katalog on 2009-08-12
FAT32 would be my choice.

---

### Post by DeMus on 2009-08-13
> **razorboy5 said:**
> Hi

I have a new External Hard Drive
so as i understand it Ubuntu uses ext3 and windows uses NFTS
i need my external to work on both Ubuntu and Windows since my brother uses Vista

what's the "best" format for that purpose?
read alot of people use FAT32 but is that good for my use?

thx

Use NTFS, it's a better format than FAT32 and both Windows and Ubuntu can read and write on it.

---

### Post by ppirilla on 2009-08-13
> **DeMus said:**
> Use NTFS, it's a better format than FAT32 and both Windows and Ubuntu can read and write on it.

Unless you really need the larger filesize support in NTFS, I strongly recommend using FAT32.  Since it has been around longer, FAT32 support is nearly universal, and I always recommend it as first choice for an external storage device.  The only downside to FAT32 is if you need to be able to store files in the 2+GB range on the device.

---

### Post by aysiu on 2009-08-13
FAT32 cannot store files bigger than **4 GB**, not *2 GB*.

---

### Post by andrew.46 on 2009-08-13
Hi razorboy,

> **razorboy5 said:**
> I have a new External Hard Drive
so as i understand it Ubuntu uses ext3 and windows uses NFTS
i need my external to work on both Ubuntu and Windows since my brother uses Vista

what's the "best" format for that purpose?
read alot of people use FAT32 but is that good for my use?

I had the same question just recently with a nice external Western Digital drive which came from the factory with fat32 file system. The deal maker for me was that:

[LIST=1]
[*]I needed to use this drive on a few different windows systems as well as my linux systems
[*]I needed to routinely transport a couple of 8gig isos
[/LIST]

Thus for me ntfs was the answer as it seemed to be the lowest common denominator and I 'formatted' the drive quickly and painlessly on a windows xp system. So it depends on your *exact* needs.

BTW I should note in passing that I believe the new *default* filesystem for Karmic Koala will be ext4 not ext3, times move on...

All the best,

Andrew

---

### Post by P4man on 2009-08-13
There is no really good solution. 

NTFS is not bad as such, but I find the NTFS-3G driver write performance really sucks on ubuntu, it hogs the cpu,  and each time its not closed properly, you can't safely or easily mount it from ubuntu.

FAT32 is problem free, but doesn't support files larger than 2? 4? GB. so thats a non starter for me.

What I ended up doing was using ext3 and installing an Ext driver for windows:

[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)

Thats not a great solution if you intend to share the drive with other windows users though, but it works well for me.

---

### Post by Wim Sturkenboom on 2009-08-13
I guess it is already formatted (FAT32 probably). If so, use that till you run into its limitations.

Don't use ext4 for an external drive as it's *not yet* universally supported so you might have problems using it on other PCs; just my 2 cents.

---

### Post by razorboy5 on 2009-08-13
alright thx for all the replies

i think i'll try NTFS, with the limit i dont think FAT32 will be very useful to me

---

### Post by scouser73 on 2009-08-13
+1 for NTFS

---

### Post by DaithiF on 2009-08-13
+1 for ext3 and convince your brother to switch to linux :)

---

### Post by swerdna on 2009-08-13
+1 for NTFS, a great filesystem

---

