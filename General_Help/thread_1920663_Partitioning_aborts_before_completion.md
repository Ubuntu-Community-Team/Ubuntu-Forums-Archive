---
title: "Partitioning aborts before completion"
date: 2012-02-05
forum: General Help
---

### Post by Ketman on 2012-02-05
I'm upgrading from 9.10 to 10.04. I made an installation disk and chose  the option to have the old and new versions with their own partitions.  It said the process would take "quite a long time". During the resize,  the activity bar went up as far as 50% in the first half minute, then  stopped. I left it for half an hour but then decided nothing more was  going to happen, so I re-booted. Have I done something wrong?

---

### Post by dcstar on 2012-02-06
> **Ketman said:**
> I'm upgrading from 9.10 to 10.04. I made an installation disk and chose  the option to have the old and new versions with their own partitions.  It said the process would take "quite a long time". During the resize,  the activity bar went up as far as 50% in the first half minute, then  stopped. I left it for half an hour but then decided nothing more was  going to happen, so I re-booted. Have I done something wrong?

Boot off an Install CD/USB and do a check on all the partitions, then use **gparted** to resize your partitions before you do the install.

Make sure you don't already have 4 Primary Partitions otherwise you will not be able to create another one in the free space.

---

### Post by efflandt on 2012-02-06
It depends upon the drive size and what is on it.

Moving the end of a partition usually does not take vary long, other than moving files down if shrinking it.

But moving the beginning of a partition can take many hours (think overnight or longer), since it involves the entire directory structure.

If you let the installation repartition automatically, you don't really know how it was trying to reorganize everything.  I always resize or create partitions before starting the install.

It is best not to interrupt it, especially by hard shutdown or forced reboot because files may be partially moved and possibly unrecoverable.  Can you still boot it ,or if you mount it are the contents of all files still valid?

---

### Post by Ketman on 2012-02-07
Thanks for the replies. After I posted my message I tried again and got the same result. An apparent freeze when the operation was 50% done. But I left it while I went out shopping and when I came back two hours later the process was completed. It looks like it was working, but just took a long time.

Today, I decided to go with the latest versiion 11.10. So I downloaded it onto CD and started again. I wanted to make partitions so I could install Windows some time in the future, but the dialogue boxes that came up convinced me that I hadn't a clue what I was doing, so I just did a fresh install of the new version using the whole disk. It's up and running now.

Is there a downloadable manual of some sort that could walk me through the whole process of partitioning, so that (for example) I have some idea what "ext 4" means, or what I have to do when I get a message like "No root file system is defined. Please correct this from partitioning menu"? Failing that, is there a book I could buy? At the moment I'm a blind man in a dark room.

---

### Post by Ketman on 2012-02-07
I've been using 11.10 for an hour or so. Didn't like the desktop arrangement at all. And after reading threads here about serious bugs in the CD burning process, I decided to go back to 10.04. I've done a clean install, using the whole disk. But I'd still like to be able to find out about partitioning, because I'll eventually want to put a small Windows partition in there to run some old DOS programs. Seriously need some Ubuntu literature....

---

