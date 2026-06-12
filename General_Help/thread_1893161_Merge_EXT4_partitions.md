---
title: "Merge EXT4 partitions?"
date: 2011-12-09
forum: General Help
---

### Post by fallenshadow on 2011-12-09
How would this be done? I installed Gparted but it doesnt seem to give me an option to merge. The default disk tool doesn't give me any options either.

Help! My current partition is 90% full so this is quite urgent! :(

---

### Post by Herman on 2011-12-09
:) There's no option for 'merging' partitions in GParted. You'll have to do it manually.

You need to update your backup of your data which you (of course) keep on some other disk or media
Then simply copy files from the partition (file system) you don't want to the other one that you do want to keep. 
Finally use GParted to delete the partition you don't want and resize the one containing your files you do want to fill the new empty disk space. :)

---

### Post by fallenshadow on 2011-12-10
Ok I want the free space of 1 in this picture to be part of 2. So do I just click resize on partition marked as 2?

There is no data on the unallocated space so its pretty safe. 

:)

---

### Post by cryptotheslow on 2011-12-10
Looks like you need to resize the extended partition sda3 first before then resizing sda7 within it.

It will probably take a fair amount of time to do. And as with anything partition related - back up first - things can go wrong.

And why 3 swap partitions?

---

### Post by Herman on 2011-12-10
> I installed Gparted but it doesnt seem to give me an option to merge.Also you shouldn't be working on a file system while it's mounted.
You'll need to right-click on your swap areas and click 'swapoff' to unmount those, and even more to the extreme, if /dev/sad7 is really the / (or 'root) partition of the operating system you installed GParted in you probably won't be able to do anything. By the looks of your GParted screencap it is.

Remember Ubuntu is free and it's unrestricted so you can install as many different copies of it as you like. The best way to use GParted for working on your computer's hard disk(s) is to run it from another operating system. An auxiliary Ubuntu installation in in a different hard disk or a USB flash memory stick would be ideal, or even just boot your Ubuntu Live CD which you probably used for installing with.

If you're looking for a nice light-weight distro that has the most up to date version of GParted plus a number of other useful applications you might consider downloading yourself a copy of Parted Magic Live CD, (or USB).

---

### Post by fallenshadow on 2011-12-12
> And why 3 swap partitions?

The extra swap partitions were created when I was messing with partitions and trying to merge them.

So today I decided to delete the additional swap partitions. Turns out it wasn't a great idea as now my PC is not able to boot! :(

I get a message:

> 
Error: No such partition
grub rescue>


I am posting this from an Ubuntu live disk... is there any way to recover from this without doing a re-install?

---

### Post by fallenshadow on 2011-12-12
Ah my technical skills are better than I thought. Fixed my grub by using the terminal through the live CD. :)

Now I have already expanded the disk to take back the extra swap space. However I think Gparted only allows you to expand if the unallocated space is next to a **white** section of the disk partition. 

However in this picture you will see its next to the yellow **data** section of the partition. I don't think there is a way to get this space onto the Linux disk! :o

---

### Post by Herman on 2011-12-13
The yellow and white areas are no more than a graphical representation showing how full your file system is, but you are correct in your observation that it's much easier to move the 'end', (or right) of the ext file system than it is to move the start (or left) of it.

Not so long ago it was not really considered possible to 'move' that end of a partition containing a Gnu/Linux file system. 
GParted does have the ability to resize Gnu/Linux file systems and  partitions to the left and has been able to do that for some time now, but it seems to take almost  forever to do it, especially if you have a large partition containing a lot of files.

A much faster but slightly more complicated way to move the partition to the left would be to first remove all  the files, (to your backup disk or even better, to a second backup),  then resize the partition as small as possible. 
Then just use the copy and paste function in GParted  to copy the entire partition and paste it to a new location to the left. 
Delete the original copy of the partition and resize the new copy to the right, then copy the files back in again.
It's more work for the user, but if you're waiting to use the computer for something it can save a lot of time.

A problem that can happen is if you have already removed as many files  as you can and resized as small as possible, but the partition is still  to large to fit in the free space area. 
That's when GParted's ability to resize Gnu/Linux partitions (file systems) to the left comes in handy. 
It's also the easiest for the user, especially if you have lots of time and are in no hurry to use the computer for a while. (Like maybe you have some other computer to use in the meantime, or are planning on being away or asleep, etc.

---

### Post by fallenshadow on 2011-12-15
So Gparted can attach this space to the left? It seems to me that it won't allow it. :confused:

---

### Post by oldfred on 2011-12-15
You cannot attach it to the left. You have to move extended partition left and then move your ext4 partition left and expand to the right. The move to the left can take a very long time and has then a higher risk as a power failure or other issues may corrupt entire system. That is why everyone discusses good backups. You have to do this from liveCD so you can unmount & swapoff mounted partitions (little key shows mounted).

Another alternative or two. With Windows dual booting, it is better to have a shared read/write NTFS partition for any data you may want in both systems. Then you can make the Windows system much smaller like 50GB and make it read only in Ubuntu. You then can either make a Linux data partition out of the other free space or move /home into the free space.
You may then move some data from your / (root) into the data or NTFS shared partitions and have more total space. The disadvantage is you have several data partitions and have to plan or organize where you put data and how much goes into each partition. If interested in data partition(s) I have posted it many times and can link to that or post again.

---

### Post by fallenshadow on 2012-01-17
See this screenshot... I have installed 12.04 ALPHA on the center partition and deleted my 11.10 partition. I now want to merge the center partition with the unallocated space on the right.

However when I try to resize the center partition it does not seem to let me take the unallocated space.

Sorry if I am being a newbie and sucking at this! :)

---

### Post by fallenshadow on 2012-01-17
Hey I got the free space merged using the Ubuntu installer partitioner! :)

Only problem is I deleted the swap partition in the process.

Is it unsafe to use Ubuntu without a swap partition?

---

### Post by oldfred on 2012-01-17
You can manually create a swap patition and add it to fstab.

If you have lots of RAM, you may not use swap with most programs. Some things like video editing eat tons of RAM, so if you do that, then you need swap. If you have 4GB or more and only open a few standard applications you can get by.

Some also use  a swap file.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
HOWTO: Use swapfile instead of partition and hibernate 
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)

---

### Post by fallenshadow on 2012-01-19
All sorted now just the way I wanted it in the first place, thanks! :)

---

### Post by arazaxirelcinellersadolur on 2012-02-18
hi,
meanwhile, i wonder, if i use all of my hard drive space or not, but u can see at the picture all volumes of my 60gb and what makes me wonder is at the bottom of the pic which shows that there are only 2.7gb free space from 7.8gb - but which from 7.8 ?!
and i recall, that when i was install ubuntu i did part the drive into 2 parts 50 and 10, but the pic shows there 2 of 7.8gb, why?
thank u and good days linuxing

---

### Post by oldfred on 2012-02-19
@       arazaxirelcinellersadolur
Much better to start your own thread, as this is solved and not many will look at it.
You only have one actual partition of 7.8. You can have 4 primary partitions, but one primary can be converted to the extended partition which can hold many logical partitions. Your extended partition of 7.8 happens to have one logical of 7.8GB.

Basics of partitions:
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

