---
title: "remove external hard drive partition."
date: 2010-01-15
forum: General Help
---

### Post by bob brazie on 2010-01-15
I just bought a new external 1 TB HP hard drive that came with two partitions.

One larger for storage and another 700 MB partition called hplauncher as a sub-file of what shows as a CD drive called HP virtual CD 4607 which held files for windows automatic back up. Which I don't need.

Both the CD and launcher drives do not allow for deletion or formatting. The larger drive does.

I am viewing it in the Palimpsest Disk Utility that cam with my Ubuntu 9.10 clean install.

Any ideas?

Thanks, Bob.

---

### Post by audiomick on 2010-01-15
That's a new one on me.
Have you got gparted installed? I would be inclined to have a look at it with that.

You can get gparted via synaptic, or the software center I guess.

---

### Post by bob brazie on 2010-01-15
The 700 MB partition called hplauncher as a sub-file of what shows as a CD drive called HP virtual CD 460 does not show up in gparted.

Do you think there is really a CD player in the box too!!!

I would think it is a partition as there is only 930 GB showing on the one partition.

Any ideas?

---

### Post by audiomick on 2010-01-16
It is all a bit above my head, but:

I don't imagine there is a CD player in there. I could imagine a small flash chip that is set up to look like a CD, over and above the disks. It could also be a bit of the drive that is fenced off somehow.

Also, it is not at all unusual that something that is labelled 1TB, or 500GB or whatever to have an actual size that is slightly different.

I think I would be inclined to just ignore the mystery section, unless someone else can say something more informative about it.

---

### Post by bob brazie on 2010-01-16
I am inclined to agree with you about ignoring it.

I wonder if formatting the larger one would eliminate the smaller one.

Anyone else see this on new external drives with a automatic backup feature?

Thanks to all. Bob.

---

### Post by audiomick on 2010-01-17
> **bob brazie said:**
> I wonder if formatting the larger one would eliminate the smaller one

suck it and see...;)

---

### Post by bob brazie on 2010-01-17
I started the process but am confused as to what type of file to use.

Any suggestions?

---

### Post by audiomick on 2010-01-17
If you are absolutely certain that you will never want to use the drive with a windows computer, choose a Linux system. Ext4 is the default filesystem for 9.10, 9.04 was still using ext3. Ext2 uses a bit less space for itself, which shouldn't be an issue with a 1TB drive.

here is a wikipedia article on ext2
[http://en.wikipedia.org/wiki/Ext2fs](http://en.wikipedia.org/wiki/Ext2fs)
with links to further articles about ext 3 and ext 4. Skim through that if you want to know a bit more about the pros and cons.

If you want the HD to be able to talk to windows, use NTFS, or maybe even the older FAT32.

---

### Post by bob brazie on 2010-01-17
Thanks for the information. It does need to talk to windows installs so I will use the NTFS.

Again, Thanks for all your help.

Bob.

---

