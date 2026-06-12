---
title: "Migrate existing filesystem to LVM?"
date: 2011-03-10
forum: General Help
---

### Post by demonioardente on 2011-03-10
I recently got a new hard drive to add another 2tb to my file server.. (I store all my files in a directory separate from the normal linux directories)
Thing is, as I was moving files to the new drive to free space on the old I remembered something about LVM letting me just use it as one big volume (i.e. combining it with the existing one to make a ~3tb volume)

So what I want to know is it possible to create an lvm on the 2tb drive, without destroying the ext4 filesystem and its associated files?
From there I would want to copy what was left of the data on the 1tb to the lvm, backup the normal linux tree /bin /var /usr /etc and so on, backup/repartition the 1tb so that the linux tree is out of the lvm (because I'm more comfortable that way) and then add the rest to the lvm...

So, if that was easy enough to follow, is this possible? I really do not want to reinstall again... nor do I want to put the drive it replaced back in (a 250gb)

I know there is search and what not, but was overwhelmed by the info...

---

