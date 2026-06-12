---
title: "low disk space, lack of controllers"
date: 2009-10-29
forum: General Help
---

### Post by i.r.id10t on 2009-10-29
Ok... so I have this box with 2 sata drives in software RAID-1 that I use to create a local apt mirror for Ubuntu and Debian.  I'd like to mirror 9.10 as well, but I only have 15gb of space left.

So, I'm holding a few 120gb sata drives in my hand... BUT I only have 2 sata controllers in the box.

What is the best way for me to increase the size?  Should I just reinstall?  Give up RAID-1, break the mirror, leave one of the original disks in and add a single 120?

Oh, and no budget, so while adding an extra SATA card would be quick and easy, I don't have a budget.

---

### Post by phillw on 2009-10-29
Hmmm... I'm having a look for you >          While GParted can identify RAID devices, it cannot create or fail them. To this end, you will have to use other         utilities. For now, though, it is important that you understand what RAID is what it looks like, so you can         properly identify the layout and change it accordingly if needed.       


So, there goes that idea.... 

I'll keep looking.

---

### Post by phillw on 2009-10-29
Ahh, that site i got that from did say that they were going to write about raid ...

They have ....

[http://www.dedoimedo.com/computers/linux-raid.html](http://www.dedoimedo.com/computers/linux-raid.html)

I've used a couple of their tutorials and found them very good, so you may want to head over and take a look.

Regards,

Phill.

---

### Post by i.r.id10t on 2009-10-29
Yeah, like I said I'm already running RAID1 on it - just need to increase the storage space.

I'm thinking right now that I may just end up doing a total reinstall ...

---

