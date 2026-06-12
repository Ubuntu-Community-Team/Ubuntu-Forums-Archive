---
title: "changing defult permissions of /dev/sdb"
date: 2010-01-04
forum: General Help
---

### Post by RancidLM on 2010-01-04
Hi, 
im looking to allow virtualbox raw disk access to /dev/sdb
currently if i 
ls -l /dev/sdb
brw-rw---- 1 root disk 8,2010-01-04 17:00 /dev/sdb

now if i chmod this to 777 or use chown to change the owner this temporarily works but after a few moments it defaults back to its original permissions.

is there a way i can define the permission?
i was thinking fstab but i can't have a mount point?
any thoughts?

Thanks!

---

### Post by jamesisin on 2010-01-04
Don't make changes in /dev is my recommendation.

Create a mount point and permit that mount point to have access from your virtual machine.

You can see how to create a mount point here:

[http://www.soundunreason.com/InkWell/?p=587](http://www.soundunreason.com/InkWell/?p=587)

The bit you want is about half way down.

---

### Post by RancidLM on 2010-01-04
> **jamesisin said:**
> Don't make changes in /dev is my recommendation.

Create a mount point and permit that mount point to have access from your virtual machine.

You can see how to create a mount point here:

[http://www.soundunreason.com/InkWell/?p=587](http://www.soundunreason.com/InkWell/?p=587)

The bit you want is about half way down.

Thanks for the quick reply Jamesisin, 
unfortunately this wont work because what im planning to do is use virtualbox and freenas and run the nas virtually and have raid work off of rawaccess.
so i need raw access to the full drive rather then a individual partition.

---

### Post by bodhi.zazen on 2010-01-04
Although you can use a raw HD with Virtualbox, the preferred method is in fact to create a virtual hard drive for Virtualbox. 

Rather then changing ownership and permission so /dev/* I suggest you use virtual hard drives, they are much more reliable then using a physical partition the way you envision.

---

### Post by jamesisin on 2010-01-04
I'd listen to bodhi.zazen.  I heard he hides his beans to keep them from flowing onto the rest of the site.

You can use my instructions to create a mount point for a RAID as well (slightly modified).  We can point you to further instructions if needed.  Just let us know.

---

### Post by bodhi.zazen on 2010-01-04
> **jamesisin said:**
> I'd listen to bodhi.zazen.  I heard he hides his beans to keep them from flowing onto the rest of the site.

:lolflag:

---

