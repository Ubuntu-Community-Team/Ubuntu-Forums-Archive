---
title: "using ubuntu to recover deleted data from NAS (RAID0/xfs)"
date: 2009-09-28
forum: General Help
---

### Post by acerunner on 2009-09-28
I have a western digital mybook world edition II. Some important data was accidentally deleted from it, and I am trying to recover it. My idea to recover it is to pull the drives out of the enclosure, place into a desktop, run Ubuntu from live cd, replicate the software RAID, and run some sort of recover software.

Some facts about the mybook world edition:
- it is linux based
- two 1TB drives
- RAID "linear" (i dont think it's striped)
- software RAID (unconfirmed, i don't believe everything i read online)
- xfs file system (again unconfirmed)

I've removed the NAS from the network to prevent further writing as soon as the files were deleted. I am a newbie to linux, so I was hoping to get some help on how to set up the RAID without formatting the existing data. Also, what kind of data recovery software can I use after replicating the RAID setup?

---

### Post by sedawk on 2009-09-29
Hello!

First make sure that you fully understand what happens
if you add the drives and then boot Ubuntu (from a Live-CD),
e.g. make sure the disks are never mounted in read-write mode!

It might be a good idea to dump the full drives and
then put them to a safe place and only work with
the dumps.
But that will be difficult with disks that big ...

I'm not aware of any "undelete" tool for unix-like file
systems like xfs - check if there is some tool especially
created for xfs!

What you might need are some tools like "foremost" or "scalpel"
or "photorec" that can analyze a file system and try
to recover data from it. But they might not work with xfs
and they might rely on continous data, so they do not
work well with unix-style file systems. Even if these tools
work they only support a limited set of file types.

Good luck!

---

