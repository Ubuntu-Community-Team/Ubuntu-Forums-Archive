---
title: "Partition Question ?"
date: 2011-04-14
forum: General Help
---

### Post by chelski4life on 2011-04-14
I recently upgraded to ubuntu, i have 110 GB or Free Unallocated space, how do i "re allocate" that space so i could use it to store stuff on again not a OS just files and folders, there was no option to re-allocate it :/

help ?
I have attached an image is that helps :)

---

### Post by cwa on 2011-04-14
can you use a partition manager (fdisk or a graphical one) to format the partition?

sorry, not on a ubuntu machine right now, so can't name a graphical one and don't know if you have gpartd or not.


cwa

---

### Post by chelski4life on 2011-04-14
> **cwa said:**
> can you use a partition manager (fdisk or a graphical one) to format the partition?

sorry, not on a ubuntu machine right now, so can't name a graphical one and don't know if you have gpartd or not.


cwa

I have Gparted, i click on it and it says 
"It is not possible to create more than 4 primary partitions"
If you want more partitions you should first create an extended partition. Such a partition can contain other partitions. Because an extended partition is also a primary partition it might be necessary to remove a primary partition first.

All the partitions i have are for windows and ubuntu 
 

and the format wont let me click on it

---

### Post by wolfen69 on 2011-04-14
If you don't have gparted, just do:
```
sudo apt-get install gparted
```
then
```
gksu gparted
```
then after gparted opens, select the unallocated space from the pull down menu in upper right. Just right click the partition and the rest is pretty much self explanatory. Make sure to click apply before exiting.

---

### Post by wolfen69 on 2011-04-14
> **chelski4life said:**
> 
 

and the format wont let me click on it

You need to be root to use it.
```
gksu gparted
```

---

### Post by chelski4life on 2011-04-14
> **wolfen69 said:**
> If you don't have gparted, just do:
```
sudo apt-get install gparted
```
then
```
gksu gparted
```
then after gparted opens, select the unallocated space from the pull down menu in upper right. Just right click the partition and the rest is pretty much self explanatory. Make sure to click apply before exiting.



The thing is thou its a partition, ive attached an image to show what i mean, thanks for taking the time to help i dont wanna lose 110GB of space :)

---

### Post by plucky on 2011-04-14
You are only allowed 4 primary partitions.The extended partition counts as one of the primary partitions.

Just increase the size of the extended partition to encompass the un-allocated space and create a logical partition.

You will need to do this from the Live CD.

Just remember to turn swap off on the Live Cd or it won't let you manipulate the extended partition if anything is mounted.

Good Luck

---

### Post by ajgreeny on 2011-04-14
You need to run a live CD and use gparted from that.  You already have an extended partition, sda4, so with gparted on the live CD, enlarge that to the end of the disk, filling the free space.  You will then see that the free space is within the extended partition and you will be able to make a new logical partition with that free space.  You will need to right click on the swap file in gparted and choose swapoff to be able to carry out any activities, as mounted partitions can not be edited.

If you want to be able to use it for both Ubuntu and Windows, format it to NTFS, then when booted back in Ubuntu, you can get the partition to automount at boot time with ntfs-config, available from the repos, or with a simple edit (as root) of /etc/fstab.

Come back for more details if you need to after making the new partition.

---

### Post by chelski4life on 2011-04-14
> **ajgreeny said:**
> You need to run a live CD and use gparted from that.  You already have an extended partition, sda4, so with gparted on the live CD, enlarge that to the end of the disk, filling the free space.  You will then see that the free space is within the extended partition and you will be able to make a new logical partition with that free space.

If you want to be able to use it for both Ubuntu and Windows, format it to NTFS, then when booted back in Ubuntu, you can get the partition to automount at boot time with ntfs-config, available from the repos, or with a simple edit (as root) of /etc/fstab.

Come back for more details if you need to after making the new partition.

I used a USB for my installation, so basically i need to run that off the USB and do the installtion thing and when i get to the Partition page format it to NTFS and then apply that but then cancel the installtion and i will be able to use it on windows and ubuntu ? or am i really wrong? 

Sorry for my lack of knowledge on this subject !

---

### Post by ajgreeny on 2011-04-14
No, don't go part way through the installation process.

Choose "Run Ubuntu without installing" or some similar option (I can't remember what words are used) when you boot the live USB.  That will take you to a gnome desktop without affecting your installed operating systems.  From that desktop go to **System->Administration->Gparted** and using that do what I suggest above.

That will allow you to enlarge sda4, your extended partition, and then make the new logical partition with NTFS filesystem.

Come back again if that is still too confusing to you.

---

### Post by chelski4life on 2011-04-16
> **ajgreeny said:**
> No, don't go part way through the installation process.

Choose "Run Ubuntu without installing" or some similar option (I can't remember what words are used) when you boot the live USB.  That will take you to a gnome desktop without affecting your installed operating systems.  From that desktop go to **System->Administration->Gparted** and using that do what I suggest above.

That will allow you to enlarge sda4, your extended partition, and then make the new logical partition with NTFS filesystem.

Come back again if that is still too confusing to you.


I have run the USB and Try Ubuntu, i have also opned GParted and there is no Option to extend SDA4, it is already "extended" under the file system type. Then there is a drop down and sda 5,6,7 and under it.i have tried extending all of those but it will not let me.

---

### Post by plucky on 2011-04-16
Take a screenshot of the Gparted window on the Live Cd and post it to the Forum so we can see how the disk is laid out.


> 
i have also opned GParted and there is no Option to extend SDA4, it is already "extended" under the file system type

If you have deleted the Ubuntu Partition,then your "extended Partition" has some un-allocated space within its boundaries.

If you select the extended partition **(right click on it)**,there will be an option to resize/move the partition.Select this and resize the partition so the un-allocated space moves outside of the partition.


Good Luck

---

### Post by chelski4life on 2011-04-16
> **plucky said:**
> Take a screenshot of the Gparted window on the Live Cd and post it to the Forum so we can see how the disk is laid out.




If you have deleted the Ubuntu Partition,then your "extended Partition" has some un-allocated space within its boundaries.

If you select the extended partition **(right click on it)**,there will be an option to resize/move the partition.Select this and resize the partition so the un-allocated space moves outside of the partition.


Good Luck


I have posted the image, i have tried resizing on everything it just doesn't let me :/ have i lost it forever ?

---

### Post by Zimmer on 2011-04-16
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
Essential reading...

Your space is not yet part of the extended partition.

Get the Live session of Ubuntu running from your USB stick.

Run GPARTED 

select the extended partition (ensure the swap bit of that partition is unmounted)

Use the option to grow the extended partition (sda4 in your case) and encompass the extra space you have.

Let it do that by applying the operation.

The extra space now should appear WITHIN the blue boundary of sda4, the extended partition.(Think of sda4 as a box containing logical partitions)

you may now create a further logical partition using that space (sda8 ), or add it into the existing logical partition you have(sda7) , or whatever you want.

---

### Post by oldfred on 2011-04-16
The little key symbols say you still have the partition locked/mounted. As posted above click & right click on the swap partition and choose swapoff to unmount it. Then you should be able to adjust extended partition.

---

