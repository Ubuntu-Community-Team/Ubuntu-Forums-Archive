---
title: "Using unallocated space on HD/adding to other partition?"
date: 2010-10-13
forum: General Help
---

### Post by irv on 2010-10-13
I need a little help regaining some unallocated space on my Hard Drive. I have a 52 Gib unallocated partition and I want to add it to /dev/sda4 which only has 19.73 Gib. (See attachment of my partition table). I ended up with this free space because I deleted a partition that contained another OS I no longer use. I don't know if I can use a move/resize or copy paste. I think the copy paste only copies the stored data not the space. What I want to do is take the unallocated space and add it to the sda4 partition. Can anyone help? Thanks
[ATTACH]172181[/ATTACH]

---

### Post by lukeiamyourfather on 2010-10-13
As far as I know the space must be contiguous on the disk for it to be in one partition. In other words you could expand sda5 since the unused space is next to it, but not sda4 since there's no unused space around it.

---

### Post by plucky on 2010-10-13
> Can anyone help?


You have to do it in stages.

Use Gparted on the Live CD

1) Boot Live CD and start Gparted

2) **Select swap partition and turn swap off.**It won't allow you to do anything with the extended partition when the swap partition is mounted.

3) Select /dev/sda5 and move to the right.This will take a while as it has to move the data in the partition as well.The un-allocated space will move to the front of the extended partition

4) Select /dev/sda3 and resize to move the un-allocated space out of the partition.

5) Resize /dev/sda4 into the un-allocated space that is now next to the partition.

Remember to make backups of your data before you start.

Good Luck

---

### Post by lukeiamyourfather on 2010-10-13
> **plucky said:**
> 
3) Select /dev/sda5 and move to the right.This will take a while as it has to move the data in the partition as well.The un-allocated space will move to the front of the extended partition


Crazy, I didn't know that was possible. Thanks for sharing! :)

---

### Post by irv on 2010-10-13
> **plucky said:**
> You have to do it in stages.

Use Gparted on the Live CD

1) Boot Live CD and start Gparted

2) **Select swap partition and turn swap off.**It won't allow you to do anything with the extended partition when the swap partition is mounted.

3) Select /dev/sda5 and move to the right.This will take a while as it has to move the data in the partition as well.The un-allocated space will move to the front of the extended partition

4) Select /dev/sda3 and resize to move the un-allocated space out of the partition.

5) Resize /dev/sda4 into the un-allocated space that is now next to the partition.

Remember to make backups of your data before you start.

Good Luck

OK I gave it a try, but I had one problem. In Step 2 Select swap partition and turn swap off.
I could not find where to do this. I read the help file, and it does not even mention "Swap" anywhere. I couldn't go on until I find the swap partition. 
Edit: By the way the sda5 is my Linux partition, If I move it will it change the sda5 so that my grub will not find it?

---

### Post by plucky on 2010-10-13
> In Step 2 Select swap partition and turn swap off.
I could not find where to do this.

Left click on the swap partition to select.Right click and select swapoff.

> If I move it will it change the sda5 so that my grub will not find it? 

If you move it then the UUID does not change.If you resize it the UUID will change and then you would have problems with Grub.So you should be ok.

Still,have a backup available.

Good Luck

---

### Post by irv on 2010-10-13
> Left click on the swap partition to select.Right click and select swapoff.
Do you mean Left click on the partition I want to swap? and then Right click and select "swapoff"? I just want to clarify this before I boot with the Live CD again.

---

### Post by plucky on 2010-10-13
left click on /dev/sda6 which is your swap partition.So that it is highlighted.

If it has a key symbol it is mounted.Right click and select swapoff.

---

### Post by irv on 2010-10-13
> **plucky said:**
> left click on /dev/sda6 which is your swap partition.So that it is highlighted.

If it has a key symbol it is mounted.Right click and select swapoff.

Thanks I'll give it a try.

---

### Post by irv on 2010-10-13
Well, things went well and here is what I ended up with:
[ATTACH]172217[/ATTACH]
This is what I was shooting for.
Many thanks to Plucky.

---

