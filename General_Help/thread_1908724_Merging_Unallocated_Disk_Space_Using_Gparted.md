---
title: "Merging Unallocated Disk Space Using Gparted"
date: 2012-01-14
forum: General Help
---

### Post by Tzar-Bomba on 2012-01-14
I recently formatted two partitions on an External Hard-drive and now have two different chunks of unallocated disk space. Is there any way to merge the two so I can form one single partition?

---

### Post by carl4926 on 2012-01-14
Possibly
Post a screen of it in gparted

---

### Post by imachavel on 2012-01-14
really? I'd like to know how to do that as well. But what is installed on it, an OS??

---

### Post by carl4926 on 2012-01-14
> **imachavel said:**
> really? I'd like to know how to do that as well. But what is installed on it, an OS??
Yes
But it will depend on where the free space is and where you want to merge it to
Let me see the partition table in gparted. It should show the unallocated space too

---

### Post by arroyocallejas on 2012-01-15
Hey I have the same problem, this is a snapshot of my GParted status. I want to use only one partition.

[IMG]http://img84.imageshack.us/img84/8393/screenshotoxf.png[/IMG]

---

### Post by carl4926 on 2012-01-16
> **arroyocallejas said:**
> Hey I have the same problem, this is a snapshot of my GParted status. I want to use only one partition.

[IMG]http://img84.imageshack.us/img84/8393/screenshotoxf.png[/IMG]
Your whole partition table is a mess
The large unallocated space 276GB is 
You don't need 2 swap partitions.
Use a Live CD and GParted
Delete sda7
Resize sda6 to take up that free space on the right and Apply
Now highlight sda2 Extended and resize and drag the slider all the way to left - Apply
Now Highlight sda6 and resize and drag the slider all the way to the left - Apply (this takes a long time)
That's it

However. I would prefer to see you do this:
Delete sda7
Create a ext4 partition in the 276GB free space and install Ubuntu there
Get it up and running and harvest your files etc from sda6
Once you have all your files in your new install
Use GParted in a Live CD to
Delete sda6
Resize sda2 extended to just contain swap
This will leave free space next to your new install
You can then resize this to take up all the free space from deleting sda6

---

### Post by Mark Phelps on 2012-01-16
To answer your original question -- NO.  The two unallocated spaces have an allocates space between them.

Besides, they  are only 1MB each -- and that is most likely due to rounding on partition creation. 

With that little space, I would simply leave it alone.

---

