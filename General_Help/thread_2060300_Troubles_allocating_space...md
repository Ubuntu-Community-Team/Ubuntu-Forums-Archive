---
title: "Troubles allocating space.."
date: 2012-09-19
forum: General Help
---

### Post by pyrokinetic on 2012-09-19
I decided to take the plunge and remove my Windows 7 install today and thus far everything has gone smoothly, my main problem is that I now have a LOT of unallocated space that I can't seem to use. :\

I booted GParted from a LiveUSB and turned my swap off, but when I try to 'Resize/Move' my sda6 or sda7 I can't do anything with the sliders, they move a little to the left or a little to the right, and rather than GIVE me space it just wants to TAKE space from me. :\ 

I've included a screenshot so it might explain the problem. I have a feeling it's something to do with the unallocated space appearing 'in front' of everything else, but I can't 'move' everything to the left like I've heard mentioned in other posts. I really hope some of that made sense..

Big thanks to anyone who can help.

---

### Post by twipley on 2012-09-19
What about highlighting the unallocated 417.65 GiBs, then creating another logical partition in the extended one -- is that feasible?

---

### Post by pyrokinetic on 2012-09-19
> **twipley said:**
> What about highlighting the unallocated 417.65 GiBs, then creating another logical partition in the extended one -- is that feasible?

Feasible....absolutely, but I don't really want to do it as I'm running out of space on root (I keep getting warnings about running out every time I boot) so I'd really just like to make that bigger, but I can't figure out how.

---

### Post by pyrokinetic on 2012-09-20
I think this has something to do with other posts I've seen involving somehow moving the unallocated space to the end of the disk, from there it seems others have been able to then use the space. If I could get a really, REALLY basic guide as to how I do that then I'd be exceedingly grateful. :)

---

### Post by Tobeus on 2012-09-20
What is /sda5?  It's only 450MB(ish).  Is that a necessary partition?  If that one is there, I don't think You can resize /sda6 to take up space on the other side of that partition.  I believe the space has to be contiguous.  You might be able to drag it to the left to be at the beginning if it IS a necessary partition, and then resize /sda6.  It's been a long time since I had this problem, so I may be off my rocker, hehe.

Also, which partition is your root partition?  Just curious.

-Tobeus

---

### Post by pissedoffdude on 2012-09-20
I think you're going to have to move that unallocated space to the end with Gparted or whatever you prefer.  You should be able to do this if the partitions are unmounted.  Have you tried the Gparted livecd?

Edit: By the way, have you tried resizing sda3 first, then the others?

---

### Post by Tobeus on 2012-09-20
Also, if you can't use the sliders, you should be able to right-click on the partition in the lower part of the GParted screen and select Resize/Move.  You have to start with the earliest partition in the list and move it to the beginning if I remember correctly.

Not sure if resizing /sda3 is going to work since that is the entire extended partition though.  Moving the /sda5 to the beginning should open things up for /sda6 to move and so on.

I searched around for a help guide, but there's not much out there for your particular scenario that I found.  The closest thing I found was [http://askubuntu.com/questions/126153/resizing-partition-size-on-ubuntu-12-04](http://askubuntu.com/questions/126153/resizing-partition-size-on-ubuntu-12-04) which doesn't talk about moving the free space to the end, but shows how resizing works like a chain of partitions.  Either way, I hope you get it figured out.  Let us know how it goes!

-Tobeus

---

### Post by pyrokinetic on 2012-09-20
> **Tobeus said:**
> Also, if you can't use the sliders, you should be able to right-click on the partition in the lower part of the GParted screen and select Resize/Move.  You have to start with the earliest partition in the list and move it to the beginning if I remember correctly.

Not sure if resizing /sda3 is going to work since that is the entire extended partition though.  Moving the /sda5 to the beginning should open things up for /sda6 to move and so on.

I searched around for a help guide, but there's not much out there for your particular scenario that I found.  The closest thing I found was [http://askubuntu.com/questions/126153/resizing-partition-size-on-ubuntu-12-04](http://askubuntu.com/questions/126153/resizing-partition-size-on-ubuntu-12-04) which doesn't talk about moving the free space to the end, but shows how resizing works like a chain of partitions.  Either way, I hope you get it figured out.  Let us know how it goes!


-Tobeus

Oooh! I might have had a breakthrough, I was for some reason assuming that I was able to go from sda6 (or 7) and select the Resize/Move option and slide all the unallocated space from there to the left....thus making appear the unallocated space appear "last" in gparted, if that makes sense.

Turns out I had to do it slowly. I moved sda5 to the left, then sda6, then sda7, etc.....and voila. all my unallocated space is at the bottom. I THINK I'll be able to continue from here quite easily. I hope so anyway. :D Thanks for your help!

---

