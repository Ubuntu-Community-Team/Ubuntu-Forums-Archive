---
title: "Trying to resize my Linux partition"
date: 2011-03-21
forum: General Help
---

### Post by Hishighness on 2011-03-21
Hello all, when I first installed Ubuntu I intended it to just be a secondary OS with Windows 7 being my primary, but after getting frustrated with Win7 and discovering the joys of Virtualbox I've made Ubuntu my primary OS.

Problem is when I created it I only made a small amount available to the partition, because like I said I thought it was just going to be a little use item.

Now that it's my primary OS I'd like to increase the size of my partition for it as it's starting to get crowded, but I'm having problems.

I created a Ubuntu live CD and booted into that, then I opened up GParted and found the partition and clicked on Resize/Move but it will only let me shrink it, it won't let me increase the size.

I notice that the extended and linux swap partitions have the keys on them which I thought meant they were mounted, so I try to unmount them in Gparted and in bash but in Gparted the options are greyed out and in bash it says they're not mounted to begin with.

Here are some screenshots to better illustrate it.

[[IMG]http://www.imgplace.com/img98/5397/89screenshotdevsdagpart.th.png[/IMG]]("http://www.imgplace.com/viewimg98/5397/89screenshotdevsdagpart.png")

[[IMG]http://www.imgplace.com/img98/1885/47screenshotresizemoved.th.png[/IMG]]("http://www.imgplace.com/viewimg98/1885/47screenshotresizemoved.png")

[[IMG]http://www.imgplace.com/img98/3002/38screenshotrootubuntu.th.png[/IMG]]("http://www.imgplace.com/viewimg98/3002/38screenshotrootubuntu.png")

Thanks for your time. :)

---

### Post by TeoBigusGeekus on 2011-03-21
In order to do what you want, you first have to move the unallocated space next to /dev/sda5.

---

### Post by pqwoerituytrueiwoq on 2011-03-21
open gparted on live cd
unmount swap
resize extended partition
move swap parition to right (will take a few minutes)
resize main main partition

---

### Post by Hishighness on 2011-03-21
How do I unmount the swap? I've tried in Bash but it says it isn't mounted. and the option in Gparted is greyed out.

---

### Post by pqwoerituytrueiwoq on 2011-03-21
if there is no lock by it then it is not mounted thus cant be unmounted cause it already is

---

### Post by Slim Odds on 2011-03-21
> **pqwoerituytrueiwoq said:**
> open gparted on live cd
unmount swap
resize extended partition
move swap parition to right (will take a few minutes)
resize main main partition

Once swap is unmounted, there is no reason to "move" it. Just create a new one.

It's a waste of time and disk thrashing to move a swap partition. It's only temporary stuff anyway.

---

### Post by pqwoerituytrueiwoq on 2011-03-21
> **Slim Odds said:**
> Once swap is unmounted, there is no reason to "move" it. Just create a new one.

It's a waste of time and disk thrashing to move a swap partition. It's only temporary stuff anyway.
then tell him how to update is fstab file for the new partition swap partition

---

### Post by Hishighness on 2011-03-21
I don't seem to be getting the option to do what you guys are saying. Here are all the options for all the partitions.

[[IMG]http://www.imgplace.com/img140/7010/17screenshotdevsdagpart.th.png[/IMG]]("http://www.imgplace.com/viewimg140/7010/17screenshotdevsdagpart.png")

[[IMG]http://www.imgplace.com/img140/5792/24screenshotdevsdagpart.th.png[/IMG]]("http://www.imgplace.com/viewimg140/5792/24screenshotdevsdagpart.png")

[[IMG]http://www.imgplace.com/img140/638/55screenshotdevsdagpart.th.png[/IMG]]("http://www.imgplace.com/viewimg140/638/55screenshotdevsdagpart.png")

[[IMG]http://www.imgplace.com/img140/331/95screenshotdevsdagpart.th.png[/IMG]]("http://www.imgplace.com/viewimg140/331/95screenshotdevsdagpart.png")

Edit: Ah, I see now, my apologies. I had to click swapoff for the Swap partition.

---

### Post by TeoBigusGeekus on 2011-03-21
Create a new partition from the unallocated space (ext4 format) and move it above your swap partition.

---

### Post by Hishighness on 2011-03-21
Ok, just in case anyone has the same trouble in the future here's what I did.

1. Click swapoff for the swap partition.
2. Resize the extended partition to as high as it'll go.
3. Moved the swap partition to the right.
4. Resized the Linux Partition.
5. Clicked Swapon on the swap partition.

Thank you all for your help. :)

---

### Post by TeoBigusGeekus on 2011-03-21
Gee mate, we're completely worthless...
Glad to hear that you've got it sorted out.

---

### Post by Hishighness on 2011-03-22
No no, you guys got me lookin in the right place.

---

