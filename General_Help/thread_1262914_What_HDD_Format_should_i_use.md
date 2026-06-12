---
title: "What HDD Format should i use ?"
date: 2009-09-10
forum: General Help
---

### Post by M!SF!TS on 2009-09-10
**[SIZE="3"]Hello Ubuntu Forums![/SIZE]**

**[SIZE="2"]Situation:[/SIZE]** I have a 1TB External Hard Disk Drive. I use it for Back Ups. But i don't use it for only Linux Back Ups, I also use it for Windows Back Ups.

**[SIZE="2"]Question:[/SIZE]** What type of Hard Disk Drive Format should i use, That is reliable and stable, and both Operating Systems can;

1. Read
2. Write
3. Execute

Any help and/or advise is most appreciated.

Thank you

---

### Post by khelben1979 on 2009-09-10
In my opinion, [NTFS]("http://en.wikipedia.org/wiki/Ntfs") would be best. Another alternative is to split the drives with a total of 2 partitions where you can have [EXT3]("http://en.wikipedia.org/wiki/Ext3")/[EXT4]("http://en.wikipedia.org/wiki/Ext4") on the second and keep NTFS on the first one.

---

### Post by scouser73 on 2009-09-10
+1 for NTFS

---

### Post by hyperdude111 on 2009-09-10
+2 for NTFS

Best for multi OS support, Ext3 requires special drivers in windows. Ext4 is not supported in windows. Fat32 only supports file sizes up to 4 gb

---

### Post by M!SF!TS on 2009-09-10
> **khelben1979 said:**
> Another alternative is to split the drives with a total of 2 partitions where you can have [EXT3]("http://en.wikipedia.org/wiki/Ext3")/[EXT4]("http://en.wikipedia.org/wiki/Ext4") on the second and keep NTFS on the first one.

I don't like the idea of splitting the HDD in to, two partitions...I would not be able to:

1. Read
2. Write
3. Execute

under both Operating Systems.

I.E. Widows wont recognize my EXT3/4 partition. this would be making the rule i set my self not work. 

Rule:
"Both OS's must need to Read, Write, Execute the Data on the HDD"


I do like the suggestion on NTFS though, and thank you for the link to Wiki, it is more that helpful information.

#
#Question: Whats the Difference between NTFS & NTFS-3G ?
#Never mind i figured out this is just a driver...
#
#And out of the two just mentioned. What one would be more Ideal for my situation? And has anybody currently used NTFS-3G #and can report on that stability issues with it? (I.E. like the problem people are having with EXT 4)

---

### Post by M!SF!TS on 2009-09-10
> **hyperdude111 said:**
> +2 for NTFS

Best for multi OS support, Ext3 requires special drivers in windows. Ext4 is not supported in windows. Fat32 only supports file sizes up to 4 gb


What NTFS Partition though, i know their are like 4 of them.

NTFS
#NTFS-3G (nevermind this one is just a driver to allow linux to read/write to them)
NTFS ( 0 x something )
NTFS ( 0 x something else)

Or are they all relatively the same ?

---

### Post by ashwinhgtx on 2009-09-10
Just go with regular NTFS. It'll work for both OSes.

You'll have to install the ntfsprogs package from the default repos to format the drive to NTFS using gParted.
NTFS-3g is the driver which allows you to read/write NTFS partitions.

---

### Post by M!SF!TS on 2009-09-10
Okay so NTFS it is.

[SOLVED]

---

