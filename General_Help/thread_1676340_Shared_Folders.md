---
title: "Shared Folders"
date: 2011-01-27
forum: General Help
---

### Post by zombrax on 2011-01-27
Hi again,
 
Just a quick question about shares in Ubuntu..
 
I can see the share that I created in Windows when I log onto Ubuntu
 
How can I see the other way around? That is, how can the drive or the folder that is in ubuntu is made visible in Windows?
 
thanks in advance.

---

### Post by Kljuka on 2011-01-27
If this is on the same computer:
ubuntu (linux) can read NTFS (Windows) partitions
Windows can't read ext2, ext3, ext4 partitions

So: you can't make Windows read Linux partition. Maybe there are Windows programs to overcome this.

If this is on different computers:
you need to use Samba to share Linux files with windows computers.

---

