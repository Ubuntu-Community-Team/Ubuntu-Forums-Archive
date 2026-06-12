---
title: "Having Ubuntu on 2 seperate partitions"
date: 2006-05-22
forum: General Help
---

### Post by siminone on 2006-05-22
I'm currently downloading Dapper. I have  breezy on the hard drive and I want to put Dapper on a new partition for testing. 

I remember trying to do this when I was using MDV and had trouble configuring Lilo. Can this be done for Grub?

---

### Post by Mustard on 2006-05-22
Sure.  The installer for Dapper should recognise the Breezy installation on another partition and configure grub to load both Dapper and Breezy.  You can use the same swap partition for both installs, so there is no need to create a new swap partition.

---

### Post by siminone on 2006-05-22
thanks Mustard, it works like a dream!!!

The install part of Dapper is inspired, this release has to be breakthrough that desktop linux has been waiting for.

---

