---
title: "can't access partion on nfs share"
date: 2012-01-06
forum: General Help
---

### Post by DataSpy on 2012-01-06
I have two computers, a desktop and a laptop.  On my laptop I have a separate partition for my data called storage, I also have an nfs server on my laptop.  What I want to do is access my storage partion from my desktop but even though it's mounted on my laptop when I try to access the the partition from my desktop through nfs it's empty.  Any ideas?

Any help is greatly appreciated, thanks in advance!

---

### Post by Blackbird_13 on 2012-01-07
I'm not familiar with ntfs server. However I have ntfs partitions on a desktop and a laptop and am able to access to/from the ntfs partitions using ssh. I am running Lucid on both.

Are you trying to access from within a Linux OS or from within a windows OS?

---

### Post by luvshines on 2012-01-07
> **DataSpy said:**
> ... but even though it's mounted on my laptop when I try to access the the partition from my desktop through nfs it's empty.  Any ideas?

Any help is greatly appreciated, thanks in advance!

What does the nfs export entry look like ?
Also, what command did you use to mount it on the desktop ?

---

