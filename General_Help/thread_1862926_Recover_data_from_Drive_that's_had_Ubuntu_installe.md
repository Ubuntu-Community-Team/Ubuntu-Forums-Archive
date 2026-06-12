---
title: "Recover data from Drive that's had Ubuntu installed on it?"
date: 2011-10-17
forum: General Help
---

### Post by spleencheesemonkey on 2011-10-17
Hi all.
I'm hoping someone is able to help.
I've been an idiot.  Wanting to do a fresh install of ubuntu, I backed up my home directory to a seperate drive.  Unfortunately, I then installed ubuntu onto the same drive I had backed up my precious data to! :(
What's the likelyhood of being able to recover any of this information which WAS on NTFS when backed up, but now is Ext4 because of the install?  I have not used the disk since realising that ubuntu was installed on it in error.
Will testdisk be of any use?
Any help or advice gratefully received.

---

### Post by Mark Phelps on 2011-10-17
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

### Post by areeda on 2011-10-17
My question would be do you still have the NTFS partition or did you give Ubuntu the whole drive?

IF (big IF) the partition is still intact then booting from LiveCD you should be able to mount it or as Mark suggested Windows recovery tools should be able to access it.

On the other hand if you formatted the whole drive to ext4, I don't have high hopes for success.  It may not be impossible but it won't be easy.

Good luck.

Joe

---

