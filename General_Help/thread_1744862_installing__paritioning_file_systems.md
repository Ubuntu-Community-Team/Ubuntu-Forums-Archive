---
title: "installing / paritioning file systems"
date: 2011-04-30
forum: General Help
---

### Post by l3ecl on 2011-04-30
Hi 

I've always wondered what was the correct way to install an OS. A unix file system has a tree directory with root '/' being on top and its children ect, bin, usr, tmp, and dev at the bottom. 

When I install a fresh copy of ubuntu, should I put everything in '/' in a different partition besides the 'usr'? 

It's merely a rhetorical question and I would like to find out more about the topic but I wouldn't know where to begin searching. 

So how do you guys architect your pc's?

---

### Post by oldfred on 2011-04-30
Herman had some good comments.
Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

I suggest for destops, just root, swap  & /home. But I prefer a separate /data which some others disagree with. But I boot several versions of Ubuntu and want the same data without any issues on /home.

Servers are totally different and may need separate partitions. If using RAID or LVM which are more server orientated on a desktop it depends.

---

