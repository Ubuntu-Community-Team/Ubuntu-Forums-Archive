---
title: "[SOLVED] Thinking of a better partitioning scheme for my HD, opinions?"
date: 2006-05-12
forum: General Help
---

### Post by RavenOfOdin on 2006-05-12
Hey.
Let me just say that I'm trying to get this drive to a point where I can run another OS on here besides XP and Ubuntu.

The current layout of the drive is as follows:

Recovery partition for HP software and Windows: 5 GB primary
Windows XP partition: 49.9 GB primary
Linux ext3: 24 GB primary
Linux swap: 512 MB primary

Would it be possible to change the type of either the ext3 or swap and then put a primary partition in their place, for the new OS, after downsizing one of the two major partitions?

And to anyone who replies, what are your experiences with LVM?

I've been looking into partitioning software with an option for unlimited primary partitions, but the companies putting said software out all want $$.

I don't want to remove the XP partition because its needed by a few relatives, and the recovery partition isn't burned to CD yet.

---

### Post by tonyr on 2006-05-12
[QUOTE=RavenOfOdin]
Would it be possible to change the type of either the ext3 or swap and then put a primary partition in their place, for the new OS, after downsizing one of the two major partitions?

And to anyone who replies, what are your experiences with LVM?
[/QUOTE]

Yes, it is possible, but I don't know about changing the type of the ext3 fs
if there is content there that you want to save.   One approach is to use
**resize2fs** and **fdisk**.  They are both installed on my machine
by default.  Here are a couple of links (one is a man page, just in case):
[URL="http://www.die.net/doc/linux/man/man8/resize2fs.8.html"]
http://www.die.net/doc/linux/man/man8/resize2fs.8.html[/URL]
[URL="http://gotmarko.com/article/61/shrinking-a-partition-in-linux"]
http://gotmarko.com/article/61/shrinking-a-partition-in-linux[/URL]

Remember, you should always have a swap partition for Linux.  You 
might want to consider using an extended partition with logical
partitions instead of only primary partitions.

I know nothing about LVM at this point.

---

