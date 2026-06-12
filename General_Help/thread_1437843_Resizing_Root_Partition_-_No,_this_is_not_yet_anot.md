---
title: "Resizing Root Partition - No, this is not yet another &quot;I need more space&quot; thread"
date: 2010-03-24
forum: General Help
---

### Post by navneeth on 2010-03-24
Hi. I just used a bit too much for my / when installing Ubuntu... about 10 GB/GiB -- no idea what's the in-thing these days -- and now I want to begin exploring other distros, and hence would like to make room in the root partition for the new-comer. 

The partitions as they stand are as follows

```
Disk /dev/sda: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd6edd6ed

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7139    57343986    7  HPFS/NTFS
/dev/sda2            7140        8355     9767520   83  Linux
/dev/sda3            8356        8598     1951897+   5  Extended
/dev/sda4            8599       36481   223970197+  83  Linux
/dev/sda5            8356        8598     1951866   82  Linux swap / Solaris

```

Considering Google is full of "my root partition is running out of space," I would like to ask the good people here whether it is safe to *reduce* the size of the root partition. And if it can be done, do you have any words of wisdom on how to go about it? (I have a copy of System Rescue LiveCD, so that part is covered.)

---

### Post by oldfred on 2010-03-24
You can use gparted. My root is about 5-6GB and I typically recommend 10GB for those who are limited in space and 20 otherwise, but my space does not include home nor data.

I suggest a separate data partition and move all your data to that. Then root and home do not have to be very large.

I had just root and swap for three years and also had a small NTFS shared partition for firefox and thunderbird profiles so my wife had the same email whether we were in windows or Ubuntu. We are now almost fully converted to Ubuntu so with Karmic I created a new data partition and moved all the folders from /home to that and created a separate /home. home is now only about 1GB as it only has hidden settings and I make an effort to make sure programs that save lots of data go into the data directory not /home.The advantage of separate data is you can link it into every install. Home may have settings that are not compatible between different distributions so it should not be shared (you can use different logins but then it still is separate).

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of above blog (more from several of the  comments)
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

---

### Post by navneeth on 2010-03-24
> **oldfred said:**
> You can use gparted. My root is about 5-6GB and I typically recommend 10GB for those who are limited in space and 20 otherwise, but my space does not include home nor data.

I suggest a separate data partition and move all your data to that. Then root and home do not have to be very large.

I had just root and swap for three years and also had a small NTFS shared partition for firefox and thunderbird profiles so my wife had the same email whether we were in windows or Ubuntu. We are now almost fully converted to Ubuntu so with Karmic I created a new data partition and moved all the folders from /home to that and created a separate /home. home is now only about 1GB as it only has hidden settings and I make an effort to make sure programs that save lots of data go into the data directory not /home.The advantage of separate data is you can link it into every install. Home may have settings that are not compatible between different distributions so it should not be shared (you can use different logins but then it still is separate).

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of above blog (more from several of the  comments)
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

Hm; and all this time, I thought only a separate home will do just fine. Thank you for the useful suggestions and the links -- I will go through them tonight, and undertake any large-scale changes, if necessary, during the weekend. :)

---

