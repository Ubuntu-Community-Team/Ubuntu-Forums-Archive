---
title: "Improve performance with multiple hard disk"
date: 2011-08-02
forum: General Help
---

### Post by ginger_boy92 on 2011-08-02
Hello. I have been using Ubuntu in Virtualbox for quite some time.
I have 3 external hard disk that I don't really use.
The vdi image is stored inside my laptop hard disk.
I am thinking about using the external hard disk with Ubuntu to improve the speed. 
Just for fun. 
Any tips?
I'm thinking about doing a software Raid 0.
One virtual hard disk for one external hard disk.
Would it work? and will it do any good?
Another idea is to use one Virtual hard disk for different mount point thingy. 
For example hard disk A for /boot, HD B for /, HD 3 for home etc
Again, would it do any good?

---

### Post by blind2314 on 2011-08-02
> **ginger_boy92 said:**
> Hello. I have been using Ubuntu in Virtualbox for quite some time.
I have 3 external hard disk that I don't really use.
The vdi image is stored inside my laptop hard disk.
I am thinking about using the external hard disk with Ubuntu to improve the speed. 
Just for fun. 
Any tips?
I'm thinking about doing a software Raid 0.
One virtual hard disk for one external hard disk.
Would it work? and will it do any good?
Another idea is to use one Virtual hard disk for different mount point thingy. 
For example hard disk A for /boot, HD B for /, HD 3 for home etc
Again, would it do any good?
 
No, assuming these are USB2.0 connected external disks (also, quite a few external drives are 5400RPM, aka "laptop speed"). The time spent communicating between the disks by whatever software raid you implement, in addition to the bottleneck of the drives rotational speed and USB, will negate any real benefit.

---

