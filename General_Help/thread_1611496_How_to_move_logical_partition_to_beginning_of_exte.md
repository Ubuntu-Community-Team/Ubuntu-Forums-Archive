---
title: "How to move logical partition to beginning of extended partition?"
date: 2010-11-01
forum: General Help
---

### Post by eleniontolto on 2010-11-01
I have an extended partition set up with a small XBMC Live (basically a stripped down ubuntu 10.4) partition of about 5gb in ext4, a swap space of about 3gb if I remember correctly, and then two chunks of unallocated space.  

It would seem that the XBMC Live logical partition is stuck in the middle of the extended partition.  I would like to move it do the beginning so that I can create one large additional volume for storing documents and videos.  Does anybody know how this might be done? 

Note, I have triple boot set up on this computer with the aforementioned xbmc live partition, Ubuntu 10.10, and Windows 7 Ultimate, so if anybody know of an approach from either linux or windows, either way would be most helpful!

---

### Post by garvinrick4 on 2010-11-01
In gparted of a live cd (ubuntu install cd using Try Ubuntu) right click on and resize to the
beginning of Extended partition and apply (hit green arrow) then when that done takes a bit of time resize the logical partition to the size you want and what is left over fight click on left over space and make a new partition and format to ntfs so as Windows will see it as a letter. F,G,H what ever it gives it and linux will see it as a sda# and all Operating Systems can use the Partition. You must apply anything you do in gparted (hit green arrow).

---

### Post by hhh on 2010-11-01
Back up first! Anytime you resize/move partitions you run the risk of losing everything.

---

### Post by garvinrick4 on 2010-11-02
> **hhh said:**
> Back up first! Anytime you resize/move partitions you run the risk of losing everything.
I agree.

---

