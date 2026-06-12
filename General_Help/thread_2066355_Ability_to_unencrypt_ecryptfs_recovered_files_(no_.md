---
title: "Ability to unencrypt ecryptfs recovered files? (no partition to mount)"
date: 2012-10-04
forum: General Help
---

### Post by MrD_scifi on 2012-10-04
I lost my partition (damaged) when I changed between two versions of Ubuntu and unfortunately went on to create a new partition, same username, same password.  

I belatedly used Photorec and got my files back off the HDD, but all the guides I can find talk about mounting the old partition to be able to decrypt using the password I know.

Is there any way at all to decrypt the files a non-standard way when I know the access details from the partition they came off?

---

### Post by Stonecold1995 on 2012-10-04
One of the downsides of encrypting a whole partition is that it's much harder to recover files if the filesystem structure itself is corrupted.  As far as I know, if the filesystem is too corrupted you won't be able to mount it to recover the files.

---

### Post by MrD_scifi on 2012-10-05
There is no partition to recover.  I formatted (because not formatting wasn't working) and put a new /Home partition there before I realised there are tools to recover the files that are there, unless of course they were directly written over.  

Using Photorec, I now have a separate partition with many thousands of recovered files from the large partition where the /Home partition was, but they are encrypted.  Family photos, documents, articles that I appear to have no access to.  I'll hold them for now in case someone comes along and shows a way to recover them.

---

