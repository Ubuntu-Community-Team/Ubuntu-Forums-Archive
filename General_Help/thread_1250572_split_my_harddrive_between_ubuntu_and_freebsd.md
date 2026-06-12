---
title: "split my harddrive between ubuntu and freebsd?"
date: 2009-08-26
forum: General Help
---

### Post by user sam on 2009-08-26
Well, I just now dedicated my personal computer to Ubuntu Linux! woooohhooo! Go me!:guitar:
 well, I left some free space because I want to install freebsd on a different partition. really, I have more experience with openbsd, but I've seen it do some WEIRD stuff. 
 my question(s) is/are this: do I have to create more swap space just for bsd? Do I have to do something special to grub to get it to boot into either system? HAVE I LOST MY MIND? :confused::confused::confused:
Well, Thanks in advance to anyone who assists me, and thanks again to all those who helped me in the past. :KS

---

### Post by PeEllAvaj on 2009-08-26
The default type of swap used by BSD doesn't follow the same format as Linux swap.  That being said, I successfully used it a few years ago with FreeBSD, but it is a little complicated (You create a freeBSD swap slice on the BSD partition), and then you have to remake the swap signature at linux bootup, and get linux to be able to read UFS partitions.  I would think the instructions would be almost identical for OpenBSD too.

Check out [http://www.faqs.org/docs/Linux-mini/Linux+FreeBSD.html#s3](http://www.faqs.org/docs/Linux-mini/Linux+FreeBSD.html#s3)

There might be a better way, but this is what I used in the past.  Hope it helps!

---

