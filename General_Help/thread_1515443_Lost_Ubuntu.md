---
title: "Lost Ubuntu?"
date: 2010-06-22
forum: General Help
---

### Post by soccerfan2010 on 2010-06-22
I run a dual-booted XP/Ubuntu machine.

I picked up a virus on my C: (Windows) and reformatted completely.

When I used to restart my computer I would be given the option of starting Windows or Ubuntu... now I don't?

When I load up a My Computer I also noticed now that Ubuntu drive has become C: ?

If anyone can tell me what I broke it would be great... I love Ubuntu but need to deal with Windows for Office/PDF (work) stuff.

Thanks
Andrew

---

### Post by WorMzy on 2010-06-22
When you say you formatted, how did you do that? Did you format the whole disk, or just the Windows partition?

Can you boot your Ubuntu Live CD and run the following commands in a terminal (Applications -> Accessories -> Terminal):
```
sudo fdisk -l
```
```
sudo blkid -c /dev/null
```
Post the output of both here.

---

### Post by soccerfan2010 on 2010-06-22
I formatted with Windows disk, I just formatted the partition where Windows lived (C) left D (Ubuntu partition) and my storage partition.

I can still see both drives in my My Computer.  

I think I'll need to re-download the Ubuntu disk.  Give me a few moments, thanks for the help :)

Andrew

---

### Post by WorMzy on 2010-06-22
No worries. I have a couple of other questions to ask which will affect what you need to do to get your grub (boot menu) back.

Firstly, which version of Ubuntu do you have installed? Is it the latest (10.04, released this April), or one of the older versions (9.10, 9.04, 8.10, etc)?

Also, I'm assuming that you installed Ubuntu to it's own partition, but is this correct, or did you use the Windows based installer (Wubi)?

---

### Post by arubislander on 2010-06-22
I'm guessing Wubi...

---

### Post by soccerfan2010 on 2010-06-22
I did use Wubi, is there a way to properly install Ubuntu on its own partition without Wubi?

I have lots of room on my HD (300GB) right now (XP has 80 and Ubuntu has 80 so lots of room)

I'd love to do it without Wubi if possible do I need to partition remaining space and set is as NTFS or ...?

Thanks

---

### Post by soccerfan2010 on 2010-06-22
Lucid Lynx...  I just went Ubuntu a month or two ago.

---

### Post by metalf8801 on 2010-06-22
> **soccerfan2010 said:**
> I did use Wubi, is there a way to properly install Ubuntu on its own partition without Wubi?

I have lots of room on my HD (300GB) right now (XP has 80 and Ubuntu has 80 so lots of room)

I'd love to do it without Wubi if possible do I need to partition remaining space and set is as NTFS or ...?

Thanks

if you did it with wubi you wouldn't be able to give Ubuntu more then 30GB so maybe you didn't use wubi also what did you used to see when you started your computer or I should say what was the order of Operating Systems? 

if it was Windows then Ubuntu then you most likely did use wubi 

but if it was Ubuntu then recover mode Ubuntu then memory test then another memory test then Windows you must have partitioned the hard drive and if thats the case Ubuntu is still there you just need to reinstall grub 

Can you try what WorMzy suggested with a live CD because then we will know for sure how to help you 

I hope this helps 
Dan

---

### Post by WorMzy on 2010-06-22
If you formatted your Windows partition, but originally installed Wubi to a different partition, then I'm not sure how you should proceed. Theoretically it may be possible create backups of your original Wubi files, reinstall Wubi, replace the new files with the old ones, then boot into your Wubi as though nothing ever happened, but I don't have any experience in this area, so I can't say for sure whether it'd work or not.

As for moving to a dedicated partition: as far as I know, there's not currently any way of moving a 10.04 Wubi installation to it's own partition. Older versions of Wubi could use an application called LVPM, but apparently it doesn't work on 10.04 Wubi.

Unless you have a good reason not to, I recommend that you just boot the Live CD and install a fresh version of Ubuntu to it's own partition, then reinstall any applications you installed in Wubi.

---

### Post by soccerfan2010 on 2010-06-23
Oh I did use Wubi...

It was 30, not sure why I thought 80- I made the storage for Ubuntu 80gb - my apologies.  Ok I will boot from disk.  Will I have lost all the files?

Guess I'm about to find out.

Thanks again

---

### Post by soccerfan2010 on 2010-06-23
Tried running off the install disk - trying to reinstall I got an error

Setup Failed as there are too many partitions.

I can see the Ubuntu disk is still there in my XP "My Computer" and see that itis now called C: (Ubuntu) its ~30GB with 17GB full... those 17 happen to be very important and I need to find a way to get to them.  When I open files I don't see any of the .odt .pdf or .docx files I have there.  I thought by deleting Windows the Ubuntu would still run - obviously I was wrong.  

If I put Wubi on this again will it work?

I can't afford to lose those files, any suggestions here would be great!

Many thanks,
Andrew

(PS. Also couldn't get into Ubuntu with the disk as "Setup Failed likely due to too many primary partitions" or some similar wording.  Thanks again!

---

### Post by WorMzy on 2010-06-24
Like I said before, make a backup of your existing Wubi files, then reinstall Wubi. Once it's installed, copy the backup of your original Wubi over the top of the newly installed files. You should be able to access your files again when you reboot, so make a backup of them on /host (Which is your Windows partition) or a USB flash stick.

If you've already got four primary partitions on your hard drive, you can't make any more. You'll need to remove one of them, then make an extended partition. An extended partition is a special type of partition which just holds other partitions, allowing you to circumvent the four partitions-per-disk limitation of primary partitions. So make the extended partition fill as much of the disk as possible, then install Ubuntu to part of it (by booting from the Ubuntu CD and creating a new partition on the Extended partition for it).

Once you've installed Ubuntu, you can mount your Windows partition with your backed up Wubi files on it, and copy the files to your Ubuntu installation.

---

### Post by soccerfan2010 on 2010-06-27
Ok, this is exactly what I need - thanks for your help.  I still have a few questions.

*1) make a backup of your existing Wubi files, *
How do I do this?

[http://www.glowfoto.com/static_image/27-151251L/4501/jpg/06/2010/img4/glowfoto](http://www.glowfoto.com/static_image/27-151251L/4501/jpg/06/2010/img4/glowfoto)
[http://www.glowfoto.com/static_image/27-151544L/2428/jpg/06/2010/img4/glowfoto](http://www.glowfoto.com/static_image/27-151544L/2428/jpg/06/2010/img4/glowfoto)
[http://www.glowfoto.com/static_image/27-131615L/1444/jpg/06/2010/img5/glowfoto](http://www.glowfoto.com/static_image/27-131615L/1444/jpg/06/2010/img5/glowfoto)

I hosted those images on imagehosting.com so you can see what I'm looking at.  What are the Wubi files?  There is no Wubi folder?

*2)  then  reinstall Wubi. *
Just download it or do I need disk/flash?

*3)Once it's installed, copy the backup of your original  Wubi over the top of the newly installed files. *
This makes sense

*4) You should be able to  access your files again when you reboot, so make a backup of them on  /host (Which is your Windows partition) or a USB flash stick.*
I think I get it


*5) If you've already got four primary partitions on your hard drive, you  can't make any more. You'll need to remove one of them, then make an  extended partition. An extended partition is a special type of partition  which just holds other partitions, allowing you to circumvent the four  partitions-per-disk limitation of primary partitions. So make the  extended partition fill as much of the disk as possible, then install  Ubuntu to part of it (by booting from the Ubuntu CD and creating a new  partition on the Extended partition for it).*

Not sure if you could see in the firstpicture but I think I only have 3 partitions?  I also noticed that when I tried to make an Extended it wasnt an option:

check this link
[http://www.glowfoto.com/static_image/27-134437L/6064/jpg/06/2010/img6/glowfoto](http://www.glowfoto.com/static_image/27-134437L/6064/jpg/06/2010/img6/glowfoto)


*6) Once you've installed Ubuntu, you can mount your Windows partition with  your backed up Wubi files on it, and copy the files to your Ubuntu  installation.*
No idea how to do this

---

### Post by WorMzy on 2010-06-27
> 1) make a backup of your existing Wubi files,
How do I do this?

I'm not too familiar with the way Wubi works, so it's probably best to just make a copy of C:\ubuntu, you don't have enough space on that partition to do it there, so copy it to your storage partition (E:\), assuming that it has enough space.

It's possible that you only need to back up the disks folder, as that's where Wubi's root disk image is stored, but backing everything up is a safer idea.

> 2) then reinstall Wubi.
Just download it or do I need disk/flash?

How did you install it the first time around? You should be able to use the same method again.

> 5) If you've already got four primary partitions on your hard drive, you can't make any more. You'll need to remove one of them, then make an extended partition. An extended partition is a special type of partition which just holds other partitions, allowing you to circumvent the four partitions-per-disk limitation of primary partitions. So make the extended partition fill as much of the disk as possible, then install Ubuntu to part of it (by booting from the Ubuntu CD and creating a new partition on the Extended partition for it).

Not sure if you could see in the firstpicture but I think I only have 3 partitions? I also noticed that when I tried to make an Extended it wasnt an option:

check this link
[http://www.glowfoto.com/static_image.../img6/glowfoto](http://www.glowfoto.com/static_image.../img6/glowfoto)

Okay, this is where things get a little complicated. You already have an extended partition, it's around D:\ (see the green line?) I'm not sure why you've put your Windows installation on an extended partition, but it may be possible to resize the extended partition.

I think the best course of action would be to move the storage partition to the end of the disk, delete the Ubuntu partition, then extend the extended partition to fill the disk up to the storage partition. You should be able to do all this from the Windows disk manager. After you've done that you'll be able to fit your Ubuntu and Swap partitions next to the Windows partition. Just [COLOR="Red"]_make sure that you back up all your important data to an external hard drive, or DVDs, before you start messing with partitions_[/COLOR]. Disk managers are pretty good nowadays, but they're not perfect. If they go wrong, you could end up losing all your partitions, and you'll need to use data recovery software to try to recover it all from the hard disk. Oh, and make sure that the files you backed up from inside Wubi, aren't on the Ubuntu partition when you delete it, otherwise they'll be lost.

> 6) Once you've installed Ubuntu, you can mount your Windows partition with your backed up Wubi files on it, and copy the files to your Ubuntu installation.
No idea how to do this 

It's easy, once Ubuntu is installed, open the file manager (nautilus) and you'll have a list of other partitions on the hard drive listed down the left-hand side; just click on one, and it'll mount it for you, then you'll be able to copy files over to your Ubuntu partition.

---

