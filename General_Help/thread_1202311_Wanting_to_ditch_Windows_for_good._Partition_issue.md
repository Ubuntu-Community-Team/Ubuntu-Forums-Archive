---
title: "Wanting to ditch Windows for good. Partition issue."
date: 2009-07-02
forum: General Help
---

### Post by efosmark on 2009-07-02
So I've decided to remove my Windows XP partition and dedicate my whole drive to Ubuntu. I can't figure out how to remove the XP partition and extend the Ubuntu partition.

Any help?

---

### Post by AoSteve on 2009-07-02
You'll have to use a partition manager, such as gparted.  One thing however, you NEED to read up about it before you do it.  If you partition a drive, you could lose all of the data on the drive and it could become unrecoverable.  

gparted is in the repo's and you can install it like with aptitude...

```
sudo apt-get install gparted
``` 

I use it on my flash drives all the time! :)  Hope this helps bud!

---

### Post by nothingspecial on 2009-07-02
You won`t be able to do it with gparted on your pc, you will have to do it with a live cd because you can`t partition a drive that is mounted.

Boot up your live cd and go system > administration > partition editor.

Make sure you know exactly what you are doing before you do it as you could well wipe everything.

Obviously make a backup of everything you don`t want to loose before you do just incase a cockup does occur.

---

### Post by efosmark on 2009-07-02
AoSteve, I actually have that installed already. :)

The problem is that I can't seem to change the size of the Ubuntu partition.

---

### Post by alphacrucis2 on 2009-07-02
> **efosmark said:**
> AoSteve, I actually have that installed already. :)

The problem is that I can't seem to change the size of the Ubuntu partition.

That's because it's the partition that ubuntu is running off. You need to boot from the Ubuntu Live CD which has gparted (Partition Editor) included. You will then be able to change the partitions on the hard disk.

---

### Post by AoSteve on 2009-07-02
LOL  I didn't realize you said you wanted use the "whole" drive for ubuntu alone.  LOL    You'll need the live CD for it.  LOL    I was thinking like my system, it's running from different drives.  A Ubuntu Drive, a Windows Drive, and a NTFS Median drive for files.  :)

Sorry about that bud.  The Live CD will do the trick, you just need to start gparted from there and do the work.  :)

---

