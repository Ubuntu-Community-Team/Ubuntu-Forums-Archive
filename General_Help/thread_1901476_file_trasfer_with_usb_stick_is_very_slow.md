---
title: "file trasfer with usb stick is very slow"
date: 2011-12-28
forum: General Help
---

### Post by iaragorn on 2011-12-28
Hello,

i have 64bit Ubuntu 10.04. LTS Lucid Lynx, gnome version 2.30.2.
(to be more specific: Linux ubuntu 2.6.32-33-generic #72-Ubuntu SMP Fri Jul 29 21:07:13 UTC 2011 x86_64 GNU/Linux).

Problem is with transfering a big files to/from usb stick. Transfer speed started about 35 MB/sec and then fall down to 5MB/sec. And it tooks almost 4 min transfer one 1,4 GB file. 

When i tried it on the same machine in Windows, it's fast (less than 1 minute). 

Do you have any idea? What is wrong?

Thanks for answer

---

### Post by iaragorn on 2012-01-04
There is no answer on this problem?

---

### Post by QIII on 2012-01-04
This is a long-standing complaint.  Some fixes have worked for some people and not for others.  If I have some time tonight, I'll try to give you some stuff to look at.  But, as I said, the solutions seem to be hit or miss.

---

### Post by carranty on 2012-01-04
I've had this problem for nearly three years now (ever since transferring over from windows).  It is quite a common problem, I've read many bug reports on it but Ubuntu's developers just don't seem to take it seriously.  QIII is right, there are some solutions out there that are seem to work for some people, but most of us just have to live with it.

I've found that if you upload a very large file (>10GB) you'll find the write speed drops gradually until it stabilizes, but then after a while it will probably increase again.  Also the minimum speed (5MB/sec in your case) seems to vary from week to week.  Also don't let anyone tell you its your computer, I've used Ubuntu on 3 laptops and  4 desktops of different makes and specifications and its been a problem on every single one of them.

Some say to turn off USB legacy mode in BIOS
[http://ubuntuforums.org/showthread.php?t=1264580](http://ubuntuforums.org/showthread.php?t=1264580)

Others say to set up Linux Cgroups
[http://www.serverwatch.com/tutorials/article.php/3921001/Setting-Up-Linux-Cgroups.htm](http://www.serverwatch.com/tutorials/article.php/3921001/Setting-Up-Linux-Cgroups.htm)

Some say to disconnect all USB drives your not using, some say attach the stick to a powered USB hub.

Some say turn off previews in nautilus, or to change the grub boot file
[http://brainstorm.ubuntu.com/idea/15648/](http://brainstorm.ubuntu.com/idea/15648/)

There are tonnes of other 'solutions' if you google it, though I've not had any luck with them.  

One thing to  note though, if its an NTFS partition, try reformatting it to ext3 or ext4, NTFS can be quite slow in linux.

This may also be helpful
[https://bbs.archlinux.org/viewtopic.php?id=116958](https://bbs.archlinux.org/viewtopic.php?id=116958)

---

### Post by iaragorn on 2012-03-15
I recognized I have same problem under windows, so it is not problem of OS.
It is with hardware. The usb stick or my motherboard, or both together have some problem. 
Anyway thanks for advice

---

