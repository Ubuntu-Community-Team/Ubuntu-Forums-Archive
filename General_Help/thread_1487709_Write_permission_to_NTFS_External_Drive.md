---
title: "Write permission to NTFS External Drive"
date: 2010-05-19
forum: General Help
---

### Post by optix7 on 2010-05-19
Hey guys

im facing this problem with the (writing/deleting) permission to my external drive which is in NTFS Format. i have tried to use the NTFS Configuration Tool but it just stops me from accessing the drive right after i install. i get the following message

[IMG]http://img215.imageshack.us/img215/7498/67952786.png[/IMG]

i have tried the chkdsk feature and the proper shutdown and removing the drive safely from windows xp, i can view the files without any problems but not no writing deleting permissions

---

### Post by jalirious on 2010-05-19
On lucid, right?

I think there are some teething problems with ntfs compatibility on 10.04. I have a 500gb ext hd formatted (with gparted) to ntfs and it is recognised by my dell 1012, but not my old inspiron (same OS)

[http://www.aigarius.com/blog/2010/03/28/ubuntu-10-04-and-ntfs-filesystems/](http://www.aigarius.com/blog/2010/03/28/ubuntu-10-04-and-ntfs-filesystems/)

Wish I could be of more help.

---

### Post by optix7 on 2010-05-19
Well thanks for passing by,yeah it's Lucid.  do you think reinstalling 9.04 would fix the problem ?

---

### Post by jalirious on 2010-05-31
I would sit it out if poss, these cats are quick on the fix.

---

### Post by oldfred on 2010-05-31
Do not know if something is causing the problem but testdisk supposedly has a fix. I have not used it.

Part of testdisk which is in the repositories or most recovery CDs.
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

---

