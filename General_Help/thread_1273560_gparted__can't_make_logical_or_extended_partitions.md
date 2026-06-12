---
title: "gparted : can't make logical or extended partitions / gray options /screenshot inside"
date: 2009-09-23
forum: General Help
---

### Post by chriskin on 2009-09-23
i don't know if this changes anything but my partition table looks like this :
an extended partition having inside the partition ubuntu is installed in (it is just one inside the extended because of changes that i did some time ago, merging two partitions) , and 3 primary ones - one that has my music/ one with windows7 and the swap file.

i want to get 9.10 installed so i though that i could get swap and 9,10 on an extended : even if i get the space and delete the windows partition and swap, the extended option is gray

so i thought i should make swap a logical partition to be able to make a primary for 9.10 , didn't work either, i got a gray option as well - only primary was clickable

is there any way to fix this other than splitting my ubuntu partition? 

i add a screenshot to get things clearer

[IMG]http://dl.getdropbox.com/u/452182/Screenshot.png[/IMG]

---

### Post by geirha on 2009-09-23
With the default theme, those V icons next to some of your partitions, are key-icons. The key-icon means that the partition is mounted, and if any partitions on the drive is mounted, gparted won't let you alter the partition table. 

Since one of the partitions is mounted at /, you cannot do much on that drive from the running system. Boot the Ubuntu CD or gparted live CD and partition from there.

EDIT: I recommend this guide: [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by chriskin on 2009-09-23
> **geirha said:**
> With the default theme, those V icons next to some of your partitions, are key-icons. The key-icon means that the partition is mounted, and if any partitions on the drive is mounted, gparted won't let you alter the partition table. 

Since one of the partitions is mounted at /, you cannot do much on that drive from the running system. Boot the Ubuntu CD or gparted live CD and partition from there.

of course i unmounted them before trying - does the ubuntu partition (the one at /) affect what i can do with the other partitions when they are unmounted? i didn't know that - i'll boot from karmic live now, and try changes from there

---

### Post by geirha on 2009-09-23
> **chriskin said:**
> of course i unmounted them before trying - does the ubuntu partition (the one at /) affect what i can do with the other partitions when they are unmounted? i didn't know that - i'll boot from karmic live now, and try changes from there

Yes, you cannot unmount / since the operating system is running from that partition; it would be like cutting down the branch you're sitting on. So, you have to run the operating system from a different location, be that another harddrive, CD, usb or other.

---

### Post by chriskin on 2009-09-23
> **geirha said:**
> Yes, you cannot unmount / since the operating system is running from that partition; it would be like cutting down the branch you're sitting on. So, you have to run the operating system from a different location, be that another harddrive, CD, usb or other.

i have no different opinion about that, what i want though is to make the Other partitions extended or logical, why can't i make swap (once i have clicked swapoff) logical?

i chose to remove windows at this time (i'm writing through the live cd) but i would still like to know why the options on the non-mounted partitions are limited

---

### Post by chriskin on 2009-09-23
by the way, i can't make a logical or extended partition when i delete windows even through the live cd's gparted
:confused:

---

### Post by mike555 on 2009-09-23
You can only have 4 primary partitions , one of them can be a logical partition .........

---

### Post by chriskin on 2009-09-23
just one extended eh?
thanks :)
i get an idea on how to fix this now

---

