---
title: "Resize used ubuntu partition?"
date: 2010-07-21
forum: General Help
---

### Post by _h_ on 2010-07-21
Simple question. Let's say I have ubuntu installed on a 30gb partition, is it possible that I can resize it to say 50gb or 75gb in the future with ubuntu&data already located on the partition?

---

### Post by snowpine on 2010-07-21
Yes, of course. :)

You can boot with an Ubuntu Live CD and use Gparted (System->Admin->Partition Editior if my memory is correct) to resize a partition or partitions. Doing so should not destroy your data.

However, before performing any partitioning activity, it is always a good idea to back up all data to an external drive, in case of user error, power outage, disk failure, etc.

---

### Post by _h_ on 2010-07-21
> **snowpine said:**
> Yes, of course. :)

You can boot with an Ubuntu Live CD and use Gparted (System->Admin->Partition Editior if my memory is correct) to resize a partition or partitions. Doing so should not destroy your data.

However, before performing any partitioning activity, it is always a good idea to back up all data to an external drive, in case of user error, power outage, disk failure, etc.

Ok thanks. Would it in anyway affect the performance of my first partition which is Windows?

---

### Post by drs305 on 2010-07-21
No it wouldn't.

Here are some tips on how to expand /.

[Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")

Start half way down the post.

---

### Post by _h_ on 2010-07-21
> **drs305 said:**
> [Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")

Start half way down the post.


Thanks, bookmarked.

---

### Post by snowpine on 2010-07-21
> **_h_ said:**
> Ok thanks. Would it in anyway affect the performance of my first partition which is Windows?

In general, no... however, I have heard that Windows filesystems can slow down if they are getting very full. So I would make sure you have adequate space available.

I have also heard (this is the first time you mentioned Windows) that some Windows releases should be resized from within Windows, rather than from a Linux Live CD. (this would add a step to your process) I am not a Windows expert however, so I would encourage you to search for a definitive answer from a more knowledgeable expert. :)

---

