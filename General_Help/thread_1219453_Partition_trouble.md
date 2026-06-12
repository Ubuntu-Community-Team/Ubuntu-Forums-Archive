---
title: "Partition trouble"
date: 2009-07-21
forum: General Help
---

### Post by hiding on 2009-07-21
I'm having some trouble trying to change the partitioning of my disk. 

I am using a ubuntu hardy Live CD to try and alter the partitions but I keep getting an error message that I don't understand. 

Basically, I'm just trying to change things about so I can expand the space available for the filesystem, which is currently on a full small partition.

But gparted won't let me make any changes, and I don't understand why. 

If anyone could help with this it would be greatly appreciated. 

Picture attached for illustration purposes...

---

### Post by Cheesemill on 2009-07-21
Click on the arrow next to Shrink and it will give you a more detailed error message.

---

### Post by hiding on 2009-07-21
Here.

---

### Post by Cheesemill on 2009-07-21
Nearly there, click the arrow next to check filesystem.
 
Keep expanding the arrows until you see an error message :)

---

### Post by hiding on 2009-07-22
Apologies. I seem to have come over uncommonly slow-witted. 

Below is a screenshot with the error details.

The problem seems to be that the disk is mounted, though I thought I'd unmounted it.

Thoughts?

---

### Post by egalvan on 2009-07-22
> **hiding said:**
> 
I am using a ubuntu hardy Live CD to try and alter the partitions
 but I keep getting an error message that I don't understand. 

But gparted won't let me make any changes, and I don't understand why. 

...

Hardy has an older version of gparted...

I would suggest using partedmagic LiveCD, it's much more robust,
and has much newer versions...

[http://partedmagic.com/](http://partedmagic.com/)

I use it on a regular basis, and I donate to the authors.


And you need to make SURE that all partitions are un-mounted.

---

### Post by hiding on 2009-07-22
Well, I not really in a position to download big files at the moment so I think I'm stuck with the hardy CD for now.

This might be a stupid question but it seems important to get it right: what do I have to do to unmount the disk? I thought I understood this but clearly I don't.

---

### Post by egalvan on 2009-07-23
> **hiding said:**
> not in a position to download big files
 so I think I'm stuck with the hardy CD for now.

Both gparted & partedmagic LiveCD's weigh in at 95MB.

You can also buy many Linux-related CD/DVD's at 

osdisc.com

I use them fairly regularly, and they always deliver.


> 
This might be a stupid question but it seems important to get it right: what do I have to do to unmount the disk? I thought I understood this but clearly I don't.

Right-click on a drive, and the context menu should have an un-mount option.

This works inside gparted, and Nautilus file manager.
KDE-centric, I don't know the file manager, but it should have similar capabilities.

A file system must not be in use, or you can have problems.

Obvioulsy, a running Linux cannot be un-mounted, hence the use of LiveCD to make things easier. A data file system can usually be un-mounted, as the OS is probably not using it on a regular basis...

---

