---
title: "How do I add separate drive to my (encrypted) home directory?"
date: 2010-06-18
forum: General Help
---

### Post by jb5 on 2010-06-18
Ubuntu 10.04 (64)

I have a second drive (currently mounted as /disk2).

I want my home directory (/home/jb) to include this second disk as JUST a separate 'folder' accessible from my home area.

I want the data on the second disk to be encrypted, (just like my /home/jb folder is now).

I would prefer to 'blend' the second drive into my existing setup.

I'm looking for the safest way to achieve this, don't mind editing fstab etc. or getting my hands dirty on the cli.

Aside from the slight drop in performance and slight increase in file size are there any other things I need to worry about?

Many Thanks.

---

### Post by dcstar on 2010-06-18
> **jb5 said:**
> Ubuntu 10.04 (64)

I have a second drive (currently mounted as /disk2).

I want my home directory (/home/jb) to include this second disk as JUST a separate 'folder' accessible from my home area.

I want the data on the second disk to be encrypted, (just like my /home/jb folder is now).

I would prefer to 'blend' the second drive into my existing setup.

I'm looking for the safest way to achieve this, don't mind editing fstab etc. or getting my hands dirty on the cli.

Aside from the slight drop in performance and slight increase in file size are there any other things I need to worry about?

Many Thanks.

Make an encrypted partition and mount it inside your /home folder.

---

### Post by jb5 on 2010-06-18
Hi - thanks for info.

What I was hoping to be able to achieve was a file by file encryption (as I think happens now in my encrypted home folder).

If I encrypt the disk/partition, do I not run into the problem that all my data is lost if there is an error on one part of the disk, whereas using (ecryptfs?) I would only lose the individual file?

---

