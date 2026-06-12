---
title: "Trouble backing up a folder on a dead ubuntu installation"
date: 2010-03-14
forum: General Help
---

### Post by wcc17 on 2010-03-14
I recently had ubuntu as my main operating system on my computer, but that wasn't working out because iTunes just does not work on ubuntu. So I started to try to dual boot windows XP, but when I tried to create the partition, all of them crapped out on me, so now I'm left with a computer boot anything, it just goes straight to error loading operating system. Now I can't get the one folder that I need off of the ubuntu installation because I don't have permission too. Can anybody help me out?

---

### Post by dcstar on 2010-03-14
> **wcc17 said:**
> I recently had ubuntu as my main operating system on my computer, but that wasn't working out because iTunes just does not work on ubuntu. So I started to try to dual boot windows XP, but when I tried to create the partition, all of them crapped out on me, so now I'm left with a computer boot anything, it just goes straight to error loading operating system. Now I can't get the one folder that I need off of the ubuntu installation because I don't have permission too. Can anybody help me out?

Boot off a Live CD and use that to access the hard drive.

---

### Post by wcc17 on 2010-03-14
That doesn't work, it says I don't have permissions to get to the folder.

---

### Post by az on 2010-03-14
> **wcc17 said:**
> That doesn't work, it says I don't have permissions to get to the folder.

What exactly do you mean when you say you don't have permission?  Can you browse the filesystem or did the partitioner mess up the partition table and leave you with a drive whose partitions are not accessible?

If you can browse the folder, try running nautilus from the live cd with sudo privileges:

gksudo nautilus

---

### Post by wcc17 on 2010-03-14
It just won't let me open up the folder on my ubuntu desktop (the installed ubuntu) from the live CD. also, nautilus did not help, it only gave me access to the document on the live cd.

---

### Post by wcc17 on 2010-03-14
Okay, so the nautilus thing let's ke open it, but I still can't move the files.!

---

