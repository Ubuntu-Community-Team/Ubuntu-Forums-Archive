---
title: "Is Lucid NTFS-friendly?"
date: 2010-11-05
forum: General Help
---

### Post by JustGus on 2010-11-05
Hi - 
I've done a bit of googling, but can't find a clear answer on this.  If I format a USB drive using NTFS, so I can store copies of files from my Win 7 machine and my Lucid machine, will it work.
Cheers,
Gregg

---

### Post by Decatf on 2010-11-05
Distros have been ntfs friendly for quite a few years now.

---

### Post by wilee-nilee on 2010-11-05
> **JustGus said:**
> Hi - 
I've done a bit of googling, but can't find a clear answer on this.  If I format a USB drive using NTFS, so I can store copies of files from my Win 7 machine and my Lucid machine, will it work.
Cheers,
Gregg

Pretty much any Linux setup will read and write to the ntfs.

---

### Post by lightningfox on 2010-11-05
Yes it is.

I have an external hard drive formatted as NTFS and Lucid has no problem reading and writing to it.

---

### Post by Tyson S on 2010-11-05
I have 3 ntfs partitions that are read and edited daily by 10.04 and all function fully when i boot into them. Its hust like accesing an ext3 disk or uisb drive

---

### Post by Bitrate on 2010-11-05
I have found that NTFS partitions which are read and written to under Linux can get badly corrupted.

---

### Post by foxmulder881 on 2010-11-05
> **Bitrate said:**
> I have found that NTFS partitions which are read and written to under Linux can get badly corrupted.

Yeah some users claim this, yet I personally am yet to see it and/or experience it.

One of my main drives is using NTFS (because it's my old Windows XP data drive) and I've been using it in Linux for years now with no data corruption yet.
It's really only read from these days as it about ~90% full. So I rarely write anything more to it. I have 3 other drives for that! Others are a mix of ext3, ext4 and ext4 lvm.

---

### Post by dcstar on 2010-11-05
> **foxmulder881 said:**
> Yeah some users claim this, yet I personally am yet to see it and/or experience it.
..........

I would say a lot of NTFS "corruption" is due to people disconnecting external drives without properly unmounting or ejecting them with the "But I don't need to do that in Windows....." excuse.

There are forum reports of lost files etc. with dual booting, so I am wondering if things like Win 7 now do things to NTFS partitions in a manner now incompatible with Linux.

---

### Post by JustGus on 2010-11-05
Great!  Thanks for the info

---

### Post by foxmulder881 on 2010-11-06
> **dcstar said:**
> I would say a lot of NTFS "corruption" is due to people disconnecting external drives without properly unmounting or ejecting them with the "But I don't need to do that in Windows....." excuse.

Probably right there.

> **dcstar said:**
> There are forum reports of lost files etc. with dual booting, so I am wondering if things like Win 7 now do things to NTFS partitions in a manner now incompatible with Linux.

As far as I'm aware, and someone correct me if I'm wrong, Windows XP, Vista and 7 all use the same NTFS version 3.1.

---

