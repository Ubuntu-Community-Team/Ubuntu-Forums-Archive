---
title: "How to manually setup partition during install"
date: 2010-03-10
forum: General Help
---

### Post by schwabdale on 2010-03-10
Hello,
Can someone please help. I am trying to install ubuntu 9.1 on a 320 gig hard drive.
I have manually created a 45 gig partition. When I try to install ubuntu from the cd,,,
I can not install it. 

How do I have to setup the 45 gigs to install Ubuntu on it? Swap partition? EXT2?

Please give me a step by step?

Thanks

---

### Post by bumanie on 2010-03-10
This [tutorial]("http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition") is for 9.04, but the steps are the same for 9.10. Just be aware at the last step ubuntu will install grub to windows mbr, that is fine if you want a dual boot. There is an advanced button that allows you to specify which partition to install grub to. That is usually only necessary if you are running more than one linux and want to chainload a second or third linux.

---

### Post by nothingspecial on 2010-03-10
When it gets to the partitioning bit choose manual (advanced)

Don`t touch any other partitions.

Figure out which is your 45 gig one

Right click it and choose, change (or whatever it says)

Check the format box

Choose use as ext4 journaling file system

Set the mount point as /

That`s it

---

### Post by ajgreeny on 2010-03-10
Have a look at this webpage which is actually for setting up a separate /home partition (highly recommended, so consider doing that) but has a great deal of detail on the partitioning part of the installation.
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by schwabdale on 2010-03-10
Thanks for all the help

---

