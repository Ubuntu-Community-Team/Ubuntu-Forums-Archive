---
title: "Format Hard Drive C"
date: 2012-01-25
forum: General Help
---

### Post by speedruntrainer on 2012-01-25
Hello.

I just got an old computer from my work with Ubuntu 11.10 on it, but I want to format the hard drive so it's clean.

How to format the entire hard drive?
Thanks.

---

### Post by Lars Noodén on 2012-01-25
When you do an installation there will be the section on partitioning the hard drive(s).  That's where you can specify what will be erased.

---

### Post by ajgreeny on 2012-01-25
> **speedruntrainer said:**
> Hello.

I just got an old computer from my work with Ubuntu 11.10 on it, but I want to format the hard drive so it's clean.

How to format the entire hard drive?
Thanks.
What do you want to do with it after formatting it?  If you want to install another linux distro you can just do it without pre-formatting.  If you want to put Windows on it you will need to use a live cd, eg ubuntu and run gparted to delete the partitions.  Windows can not do anything if a disk is full of ext# partitions;  it needs either empty space or a fat32/ntfs partition.

---

### Post by speedruntrainer on 2012-01-25
No, I want to format the entire drive so it's clean, some other people stuff is still on there and even a password when I lock it.

I just want to format the entire drive, after this, I install Ubuntu 10.04 LTS on it from the CD I have.
So I can start clean.

---

### Post by Lars Noodén on 2012-01-25
Just use the CD.  The installation process will wipe the harddrive for you.

---

### Post by Mark Phelps on 2012-01-25
> **speedruntrainer said:**
> Hello.

I just got an old computer from my work
oh .. oh
> but I want to format the hard drive so it's clean.

How to format the entire hard drive?
Thanks.

Contrary to what some think, formatting a drive does not "wipe" it; instead, it rewrites the partition tables so the the existing files are no longer (easily) accessible.

If this were NOT true, then you couldn't use apps like Testdisk and Photorec to recover files from reformatted drives.

If you really want to WIPE your drive, then look into using dban:

[http://www.dban.org/]("http://www.dban.org/")

Also, if your "work" fully encrypted the entire drive (which they often do), you may not be able to reformat it (easily).

But, you may still be able to use dban against it.

---

### Post by Lars Noodén on 2012-01-25
In the context of installing Ubuntu on a harddrive the tools that come with the install disk do the job.  

In the context of overwritting the data that may have come with the drive, what are the advantages of dban over plain dd?

---

### Post by speedruntrainer on 2012-01-25
Ok, I just used the CD and it wiped out the disk fine.
I was actually worried about that 'downgrading' bug.

But Ubuntu 10.04 LTS is fully working now :)

The only thing I want to ask is where do you see your computer properties to know what's in it, I only know it's a Pentium 4 and harddrive 120GB, but I want more information, RAM, Video Card.

If you don't know what I mean, in Windows you just right click on Computer > Properties but this isn't the case in Ubuntu, ofcourse I tried myself before asking.. hehe.

So, how to view that in Ubuntu?

Thanks in advance.

---

### Post by BC59 on 2012-01-25
Find the application System Monitor. In the first tab there are data like RAM, processor speed etc.

---

### Post by speedruntrainer on 2012-01-25
Thanks for everything! :)
Everything is now ok!

---

