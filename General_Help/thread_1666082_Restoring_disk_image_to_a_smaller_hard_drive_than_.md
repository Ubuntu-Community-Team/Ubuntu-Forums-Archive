---
title: "Restoring disk image to a smaller hard drive than the original"
date: 2011-01-13
forum: General Help
---

### Post by RolfJB on 2011-01-13
Friends, 

I have found lot of good information here and I want to thank everyone for helping out. 

I am looking for an Open Source software making it possible to make a disk image of an Ubuntu installation as well as a Windows XP installation. 

I have checked out Clonezilla which almost solved the problem. However, the disk to which you restore needs to be the same size or bigger.  

I want to restore the whole thing to a smaller disk than the original. I am considering getting myself an SSD disk which will be considerably smaller than the 160 gb disk I have right now. 

I need it to work for Windows as well. Unfortunately I can't get rid of Windows quite yet :) I often participate in webinars on GotoWebinar and they do not support Linux ...

Your suggestions will be highly appreciated!

Best wishes

---

### Post by othiena on 2011-01-13
I am notsure this will work but I think if you find a backup software that will copy the partition you shood be able to shrink the partitions to fit on the new drive.

---

### Post by vanadium on 2011-01-13
It could probably work with dd. When placing the image back, dd will fill the new drive, then abort with an error message. The resulting partition will be corrupt, but could then probably be repaired using a partition editor and chkfs.

However, this is not at all supported, and not recommended. A much better option is to reinstall your operating system, then put the user data back. The image you currently have could indeed be mounted as a looping file system, so you can simply copy your data to the new drive.

---

### Post by RolfJB on 2011-01-13
Thank you for replying! 

I will keep looking. 

Best wishes

---

### Post by RolfJB on 2011-01-13
Thank you for your reply! 

I did not think of this command. 

I was probably not describing the situation accurately. I have a big disk right now but it contains some 5 gb right now so it would of course not fill up the smaller 40 gb or so disk. 

My concern is about the Windows partition. So far I have failed miserably when moving an installation to a new and bigger disk since the old one was filling up. I worked solely under Windows then. I used only free software like BartPE and Paragon - it would not work though 

Sigh - double sigh!

Best wishes 

Rolf

---

### Post by Mark Phelps on 2011-01-13
Image create/restore apps do just that -- create an image of a partition (or drive). So, of course, you can't then "restore" that image to a smaller drive.

Your best bet would be to use partitioning tools to shrink the current partitions down to a size where they will fit on the new drive.

For Linux filesystems, you can do this with GParted.

For MS Windows filesystems, you could download EASEUS Partition Master and use that (it's free).

---

### Post by Ad@m on 2011-01-13
Acronis True Image Home 2011, which you have to purchase but it is a great disk imaging program.

[http://kb.acronis.com/content/2770](http://kb.acronis.com/content/2770)

Acronis 2011 now supports EXT4, unlike previous releases:  [http://kb.acronis.com/content/6045](http://kb.acronis.com/content/6045)

---

### Post by RolfJB on 2011-01-13
Thank you for your reply! 

I should have thought of that myself. It is very obvious now that you say so - stupid me :)

I will give it a go. 

Best wishes

---

### Post by RolfJB on 2011-01-13
Thanks Adam! 

I have read a lot of good about Acronis but right now I would prefer to use freeware / Open Source. 

Best wishes

---

### Post by Mark Phelps on 2011-01-13
> **RolfJB said:**
> ... but right now I would prefer to use freeware / Open Source. 

Then, look into using Macrium Reflect for imaging MS Windows partitions.  Their free version provides nearly everything you need -- including the ability to burn a bootable restore CD.

---

### Post by RolfJB on 2011-01-13
Fantastic Mark! 

This is exactly what I am looking for! I will certainly check out Macrium Reflect. 

Best wishes

---

