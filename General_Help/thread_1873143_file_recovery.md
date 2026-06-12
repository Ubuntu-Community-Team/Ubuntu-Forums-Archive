---
title: "file recovery"
date: 2011-10-31
forum: General Help
---

### Post by murilstone on 2011-10-31
so, i have not used Ubuntu sense around version 6. i had to go back to windows because of work. now i have made my way back to Ubuntu and am again a noob. 

so here is my big issue im hoping someone will have some patients to help me work through. i had 3 Hard drives. one i was going to keep the windows 7 drive and another i intended to install Ubuntu on (i have a hot swap bay for these two). the third is a storage and backup internal drive. well i formated the drive for Ubuntu and placed the disk in to go ahead and install. to make a long story short i basically installed Ubuntu on my storage drive and lost all my data. immediately afterwards i shutdown and removed the drive and installed Ubuntu on the correct drive. 
i am hoping to recover the data on the BU drive but not sure where to begin. something more with a GUI would probably be best but i can follow step by steps...any suggestions??

---

### Post by oldos2er on 2011-11-01
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by Mark Phelps on 2011-11-01
In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions.

If your data was on a Windows partition, my suggestions are the following (based on my experience at doing this successfully):
1) Find someone with a working Windows PC
2) Remove your drive from this PC.
3) On the Windows PC, download and install the trial version of GetDataBack for NTFS from Runtime Software.
4) Connect your old drive to this Windows PC.
5) Run GetDataBack in deepest discovery mode -- probably best to let it run overnight.
6) In the morning, check the recovery logs and see if GetDataBack was able to find your lost files.
7) If it was, you will have to purchase it to do the actual recovery. You won't have to reinstall it; instead, they will email you an activation code which you can use to turn on the recovery feature.

And, BTW, it is not HUNDREDS of dollars for this product. Last time I checked, GetDataBack for NTFS was $80, USD.

Your data ... your money ... your choice.

---

