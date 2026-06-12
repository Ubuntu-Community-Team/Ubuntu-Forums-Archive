---
title: "Critical help! Partition Editor?"
date: 2009-08-27
forum: General Help
---

### Post by mac666 on 2009-08-27
Hey
I just Unallocated 10GB from my main partition to give it to my ubuntu partition. 
But how do i do that? I now have 10GB unallocated, but i make the ubuntu partition lager with "resize/move", only smaller

How to do?
P4man gave the answer!
Thanks

---

### Post by nothingspecial on 2009-08-27
You need to move it. You can only grow a partition one way (I think)

---

### Post by mac666 on 2009-08-27
Move what where and how? :(
EDIT: I Cant move/resize the unallocated space.... its greyed

---

### Post by wojox on 2009-08-27
Boot your live cd and open partition editior.

---

### Post by amedac on 2009-08-27
Try with Acronis live cd

---

### Post by mac666 on 2009-08-27
> **wojox said:**
> Boot your live cd and open partition editior.
I Am on live CD right now but i cannot give my ubuntu partition more space from the unallocated space...

---

### Post by P4man on 2009-08-27
Your ubuntu partition is inside an extended partition probably ? Swapoff any swap partition (right click in partition editor) then resize the extended (light blue) partition first, after that you can resize the ubuntu partition contained inside.

If that doesnt work post a screenshot of the partition editor pls

---

### Post by mac666 on 2009-08-27
> **P4man said:**
> Your ubuntu partition is inside an extended partition probably ? Swapoff any swap partition (right click in partition editor) then resize the extended (light blue) partition first, after that you can resize the ubuntu partition contained inside.

If that doesnt work post a screenshot of the partition editor pls

This is how you help a guy out in a critical situation.
Thanks man i owe you one. i will now rename this topic to give it more hits.
Thanks again

---

### Post by dk06 on 2009-08-27
I don't mess with the Ubuntu partitioner unless I want to take the preset default options, GParted Live CD makes Partitioning easy and gives you more detailed info on the partitions.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

> 
**[SIZE=3]Gnome Partition Editor[/SIZE]**

  The GParted application is the GNOME partition editor for creating, reorganizing, and deleting disk partitions.

A disk device can be subdivided into one or more partitions. The GParted application enables you to change the partition organization on a disk device while preserving the contents of the partitions.

With GParted you can accomplish the following tasks:

 
[LIST]
[*]Create a partition table on a disk device.
[*]Enable and disable partition flags such as boot and hidden.
[*]Perform actions with partitions such as:
[LIST]
[*]create or delete
[*]resize or move
[*]check
[*]label
[*]copy and paste
[/LIST]
 
[/LIST]


---

### Post by P4man on 2009-08-27
> **dk06 said:**
> I don't mess with the Ubuntu partitioner unless I want to take the preset default options, GParted Live CD makes Partitioning easy and gives you more detailed info on the partitions.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

?

gparted is the partition editor from the livecd. Its the exact same program?

---

### Post by dk06 on 2009-08-27
> **P4man said:**
> ?

gparted is the partition editor from the livecd. Its the exact same program?

From what I remember, Installing Ubuntu & partitioning from the install CD was a pain in the rear,...I ended up restarting w/the GParted Live CD

So, I know you can add GParted as an app in Ubuntu, I just prefer the Live FS b/c I am able to manipulate the disk more quickly and with less error.

---

### Post by P4man on 2009-08-27
You are slightly confused. If you do an install (ubiquiti) you have this wizard like page where ubuntu gives you the choice between resizing partitions, using whole disk, etc. If you have anything but a bog standard setup, that wizard isnt clever enough. However, there is a "manual" option there too.. guess what it does? It launches gparted.

gparted on the ubuntu live cd == gparted on gparted live == gparted you install in ubuntu =! ubiquiti

---

### Post by dk06 on 2009-08-27
> **P4man said:**
> You are slightly confused. If you do an install (ubiquiti) you have this wizard like page where ubuntu gives you the choice between resizing partitions, using whole disk, etc. If you have anything but a bog standard setup, that wizard isnt clever enough. However, there is a "manual" option there too.. guess what it does? It launches gparted.

gparted on the ubuntu live cd == gparted on gparted live == gparted you install in ubuntu =! ubiquiti

Okay, I stand corrected...just remember the Ubuntu CD "Manual" Partitioning option being different from GParted.

---

