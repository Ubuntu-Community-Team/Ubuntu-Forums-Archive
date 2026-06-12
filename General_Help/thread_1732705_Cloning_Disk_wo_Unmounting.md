---
title: "Cloning Disk w/o Unmounting"
date: 2011-04-18
forum: General Help
---

### Post by zephyr707 on 2011-04-18
Hello All,

I've spent the better part of an afternoon looking for a solution to a problem: backing up my installation of 10.10 as an image file to an external hard drive.  My research has yielded a lot of suggestions for clonezilla, dd, and partimage/particlone, but those don't seem very appealing, due to a number of issues (can't backup live, copies free space as well, doesn't handle ext4, etc).  Also why is clonezilla 150mb?

I'd like a simple solution that can clone an entire disk (used space only) to an explorable image file on a separate hard drive and be able to do it while the operating system is running on the disk.  I used to use apricorn ez gig to do this on windows and it worked like a charm, but I can't seem to find a similar solution that creates and explorable .iso image file with linux.  I've used superduer on osx, which is awesome and i wish there was something like that for ubuntu/linux.

Any help is most appreciated,
thanks!
z

---

### Post by mike555 on 2011-04-18
Have you looked into Remastersys ?

---

### Post by zephyr707 on 2011-04-18
> **mike555 said:**
> Have you looked into Remastersys ?

I have not heard of remastersys, it sounds almost perfect though!  Unfortunately I have a large virtualbox machine on the drive that I want to include and it seems as if there is a 4gb limit with remastersys ([or maybe it is a debian limitation?]("http://www.remastersys.com/forums/index.php?topic=721.msg4186#msg4186")).  Even w/o that virtual machine all my software is still over 4gb, unfortunately.  thanks for the recommendation, though, that never turned up in my searches!

---

### Post by mike555 on 2011-04-18
I believe you can exclude VB .... and the 4GB limit is on the compressed size of the .iso .

You mast have ubiquity and ubiquity-frontend-gtk installed first to have the remastersys.iso installable when you make it.

---

