---
title: "FAT32/NTFS shared partitiion affected by hibernated Win XP"
date: 2012-01-09
forum: General Help
---

### Post by juchuchuuu on 2012-01-09
Hello everyone, I have got a misterious problem. 

As I understood, partition that is separated from Windows installation partition can be read and write to from both Linux and Windows even if Windows is hibernated.

I have 4 partitions - Windows XP installation, Xubuntu 11.10 installation, swap and a shared FAT32 partition. I wrote many GBs of data to the shared partition from my Xubuntu while Win XP was hibernated and after I went to Windows system, no data was present there. Then I ran Recuva and find only a small part of the all data. After that I jumped back to Xubuntu and found out that data was still there. At the moment I am backing up all the files to the external HDD in Xubuntu.

Same happened to me with shared partition of NTFS type.

So my question is, what am I doing/done wrong? I want to use shared partition with win xp hibernated, but not with this great risk. How can I resolve it?

btw.:
I used Pardted magic to create all the partitions.
I installed xubuntu-desktop with "--without-recommends" argument from alternate Xubuntu CD.
I installed every other package which I needed manually.

thank you very much for any help

---

### Post by Basher101 on 2012-01-09
it is never a good idea to run dualboots while the other OS is hibernating...as for the files not appearing, i do not know what to do there...

---

### Post by juchuchuuu on 2012-01-09
I thought, that writing to the shared partition is ok even if the other OS is hibernated. Ok then, I will have to try not to use hibernation at all...

As for the data, I did not express myself clearly. In Xubuntu, I fortunately see and can backup ALL the data I wrote to that partition! :)

thank you

---

### Post by Mark Phelps on 2012-01-09
On a Windows box, it will save the directory information of all Windows filesystem partitions that were in use when it was Hibernated.  Then, when it awakens from Hibernation, it rewrites those filesystem directories -- effectively wiping out any changes you made.

As already said, it's never a good idea to write to shared filesystems when the owning OS is hibernated.

---

### Post by Double.J on 2012-01-09
> **Mark Phelps said:**
> On a Windows box, it will save the directory information of all Windows filesystem partitions that were in use when it was Hibernated.  Then, when it awakens from Hibernation, it rewrites those filesystem directories -- effectively wiping out any changes you made.

As already said, it's never a good idea to write to shared filesystems when the owning OS is hibernated.

+1, hibernation isn't designed for OS hopping - if it were two linux distros, you'd really want 2 swap partitions on your drive! 

As mark phelps said - you wouldn't make changes to windows C drive whilst it was hibernated, and to windows, your shared partition is just another windows drive.

---

### Post by juchuchuuu on 2012-01-09
I understand now. Thank you both for your explanations.

---

