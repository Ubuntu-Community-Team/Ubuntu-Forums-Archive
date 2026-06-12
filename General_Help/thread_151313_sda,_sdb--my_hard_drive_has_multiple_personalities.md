---
title: "sda, sdb--my hard drive has multiple personalities"
date: 2006-03-27
forum: General Help
---

### Post by garren on 2006-03-27
I am running Windows on the internal hard drive of my laptop, and Breezy on a partition of an external USB drive (with Grub on the external).  When I turn on the external drive while I have Windows running (from the internal), shutdown, and then attempt to boot Linux off the external--the external drive is recognized as sda.  BUT if my computer is already powered down, and then I turn on the external drive, and attempt to boot Linux off the external--the external drive is sdb.  

Why is this happening?  

What I have done--I have two kernals available in Grub (as well as the rescue ones, etc).  One leads to sda, the other to sdb; so that way I don't have to change the boot path based on how I am starting up, I just choose the proper kernel.  

But still--why is this happening?  Is there a way I can make it stop?

---

