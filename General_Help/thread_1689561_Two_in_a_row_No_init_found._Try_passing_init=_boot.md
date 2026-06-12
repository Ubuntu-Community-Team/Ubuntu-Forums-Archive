---
title: "Two in a row: No init found. Try passing init= boot arg"
date: 2011-02-17
forum: General Help
---

### Post by Willberto on 2011-02-17
I've tried searching through the forums and picked up a couple things that are exactly related to my problem.  

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1682038](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1682038)

I had this exact problem on my friend's laptop, oddly enough it happened to both of ours within a day or so of one another's.  Unbelievable that it happened to both at the same time. though it probably happened through shutdown/wake/hibernate that froze.  I fixed it with the above post.  

My laptop gave the same messages but I think the reason why it's not working is because I have logical partitions in a container and my friend's had a straight drive with swap.

When I run sudo debugfs -w /dev/sda6   (which is inside sda3)

I get:

ubuntu@ubuntu:~$ sudo debugfs -w /dev/sda3 (or 6)
debugfs 1.41.12 (17-May-2010)
/dev/sda3: Attempt to read block from filesystem resulted in short read while opening filesystem
debugfs:  clri <8>
clri: Filesystem not open
debugfs:  quit

I try all the usual fixes though it never actually lets me mount the filesystem to check it, as from my reading there's some flag that tells it not to because it's in use.

I could be off base, but this is where I've got so far.  I think the next question is, how do I do the above with logical partitions?  Though I could be wrong about that too.  Thanks for any help offered!

---

