---
title: "which version of clonezilla do I use?"
date: 2009-09-25
forum: General Help
---

### Post by porchrat on 2009-09-25
Hi all

I run 8.04 64bit and I am looking at using clonezilla to replace a RAID array with one single drive.

I was wondering which version should I download. The english on the Clonezilla site is not very clear (English is not his first language and it is perfectly understandable).

There is an alternative version that is apparently "ubuntu-based" as opposed to "debian-based", but that doesn't necessarily mean that one is designed for Ubuntu while the other is designed for debian.

Just wanted to know if anyone had any experience with CloneZilla and how I should go about it.

---

### Post by mike555 on 2009-09-25
I have used Clonezilla from the "PartedMagic" live cd and it worked great .....  [http://partedmagic.com/](http://partedmagic.com/)     ... I'm not sure you can clone a running system , but I could be wrong...

---

### Post by Minsky on 2009-09-25
I use Clonezilla on Jaunty and there is an alternative Ubuntu version which is titled **clonezilla-live-20090919-karmic.iso** but I've no idea how compatible it is with previous versions of Ubuntu, you could try it and see if it makes a successful image. For the safest bet, you could download the current stable version which is **1.2.2-26** which should work with all versions of Ubuntu. I also found this on their Q&A page:-

Does Clonezilla support RAID ?

Clonezilla does support hardware RAID, if your RAID device is seen as /dev/sda, /dev/sdb, /dev/hda, /dev/hdb, /dev/cciss/c0d0... on GNU/Linux. Clonezilla does support this.
On the other hand, if it's Linux software RAID, no, Clonezilla does not support that.

I don't know if it will work with your set up as I've no experience of using RAID arrays

---

### Post by porchrat on 2009-09-25
> **Minsky said:**
> I use Clonezilla on Jaunty and there is an alternative Ubuntu version which is titled **clonezilla-live-20090919-karmic.iso** but I've no idea how compatible it is with previous versions of Ubuntu, you could try it and see if it makes a successful image. For the safest bet, you could download the current stable version which is **1.2.2-26** which should work with all versions of Ubuntu. I also found this on their Q&A page:-

Does Clonezilla support RAID ?

Clonezilla does support hardware RAID, if your RAID device is seen as /dev/sda, /dev/sdb, /dev/hda, /dev/hdb, /dev/cciss/c0d0... on GNU/Linux. Clonezilla does support this.
On the other hand, if it's Linux software RAID, no, Clonezilla does not support that.

I don't know if it will work with your set up as I've no experience of using RAID arrays

hmmmmmm... that is not good news.

My RAID system is software RAID (I used dmraid).

I may need to find another way to do this then.

> **mike555 said:**
> I have used Clonezilla from the "PartedMagic" live cd and it worked great .....  [http://partedmagic.com/](http://partedmagic.com/)     ... I'm not sure you can clone a running system , but I could be wrong...

Technically it wouldn't need to be running if I could get it to target an individual device instead of cloning the whole system (I'm not sure if clonezilla is capable of that). The particular drive I'm trying to clone just contains data really. The / and /home partitions are on other drives so it is easy for me to just unmount the drive and do the clone.

---

