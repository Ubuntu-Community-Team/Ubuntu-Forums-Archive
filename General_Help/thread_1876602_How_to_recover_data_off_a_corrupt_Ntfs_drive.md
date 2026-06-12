---
title: "How to recover data off a corrupt Ntfs drive?"
date: 2011-11-06
forum: General Help
---

### Post by qwertykeyman on 2011-11-06
So through this thread [http://ubuntuforums.org/showthread.php?t=1875823](http://ubuntuforums.org/showthread.php?t=1875823)
I was able to find out how to change the file type of my drive to ntfs, but now I cant access the data on it, are there any recovery programs what work well and are reliable?
(I need to ask here due to the plethera of options out on the internet I have no idea which ones are good)

Thanks

also testdisk says "Can't Open Filesystem. Filesystem seems damaged...

---

### Post by gandaran on 2011-11-06
> I was able to find out how to change the file type of my drive to ntfs, but now I cant access the data on it
if you did change the file type then you formatted the disk again making it more difficult to recover any files, I don't think you can do it with any free recovery software.

---

### Post by qwertykeyman on 2011-11-06
Well, I couldnt find any program that could allow you to get the data off of a swap drive, but reguardless even if it is not free I am willing to purchase a program, might you have any suggestions?

I saw that EnCase seemed like a good program to get the data off, even if I need to be "resourceful" to aquire it. ;)

---

### Post by Mark Phelps on 2011-11-06
In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions.

Since your data was on a Windows partition, my suggestions are the following (based on my experience at doing this successfully):
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

