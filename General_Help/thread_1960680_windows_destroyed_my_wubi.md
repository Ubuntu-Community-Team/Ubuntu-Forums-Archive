---
title: "windows destroyed my wubi"
date: 2012-04-17
forum: General Help
---

### Post by dmmusselm on 2012-04-17
Hello

I had downloaded and installed wubi about a month ago, dual booting with windows 7 pro and everything was working fine, until about an hour ago when windows 7 started running chkdsk on boot while I had walked away.  I came back to find it about 70% done just going to town with "deleting <enter file name here>".  After successfully logging in to windows, i tried to reboot into ubuntu to no avail, it goes straight to grub.  After poking around a bit, i found C:\ubuntu\disks\root.disk, which was last modified 12 hours ago (when I had last shut down my machine), to be 0 kb.  I've tried using ext2explore to explore root.disk and swap.disk, but that gives errors in the log saying 

Error Reading the MBR on C:/ubuntu/disks/root.disk 
No valid Ext2 Partitions found in the disk image.Error Opening \\.\PhysicalDrive2. Error 

Partition Table Error on C:/ubuntu/disks/swap.disk
Invalid End of sector markerBad Super Block. The drive  is not ext2 formatted.
No valid Ext2 Partitions found in the disk image.Error Opening \\.\PhysicalDrive2. Error 

Am I completely screwed?  I also searched for my old root in C:\found000 and C:\found001, these were not recently updated and did not contain anything of value.

I had a few programs and other scripts I had written the past month in ubuntu that I would really appreciate getting back.

Thanks in advance for any ideas!

---

### Post by jadtech on 2012-04-17
on this forum some whereI have seen this type of thing before where chkdsk  will some times make wubi ubuntu root.disk A hidden file you have to make hidden files visable  now where you might find  the root.disk hiding  I dont know ..

check out this thread the advice and help to find it is here 

[http://ubuntuforums.org/showthread.php?t=1770239&highlight=chkdsk+make+root+hidden+file](http://ubuntuforums.org/showthread.php?t=1770239&highlight=chkdsk+make+root+hidden+file)

hope this helps

---

### Post by dmmusselm on 2012-04-17
Thanks for the reply.  Unfortunately my root.disk was not where that post suggested.  I just find it odd that I do in fact have a root.disk, its just 0 bytes.  That's why I'm kinda concerned that it was just mutilated and is now corrupt.

---

### Post by jadtech on 2012-04-17
not sure why chkdsk this I find it interesting , I have been running awubi install for about 7 weeks or so now and one thing I have noticed is  that when I use Ubuntu for about 3 weeks without booting into windows then I boot windows I find it very bogged and the drive is 45% to 50% fragmented I have found this twice after using ubuntu for a few weeks..

maybe being so fragmented chkdsk finds the bit of lost data of root.disk and puts then together in lost and found ..

I at first was thinking since it wubi installs andi is a windows program windows would run normal tasks as scheduled this dont seem to be the case at all ..

---

### Post by jadtech on 2012-04-17
> **dmmusselm said:**
> Thanks for the reply.  Unfortunately my root.disk was not where that post suggested.  I just find it odd that I do in fact have a root.disk, its just 0 bytes.  That's why I'm kinda concerned that it was just mutilated and is now corrupt.

have you tried booting with live disk and looking in to see ???

---

### Post by jadtech on 2012-04-17
to be honest im not sure windows would read amount of disk usage for your root.disk as I understand it its just a bubble of space that grows to the point you have set it to when you installed  that windows simplly will not read from or write to..

I have never checked it the folder or file in windows myself .. 

how ever if you go to web the ubunetu website and get the ISO burned to a CD you can boot Wubi and at least copy the files you would like to save  if you have to reinstall ..

---

### Post by dmmusselm on 2012-04-18
i'm not quite sure I understand where my files are saved that I'd like to keep.  I downloaded and created a cd and am currently running ubuntu from the disk, where would i find my old files?  I thought they were in the root.disk image that no longer seems to exist.

---

### Post by jadtech on 2012-04-18
your files with the wubi install will be on your C drive or what ever letter  the drive is for your computer , I think once in live disk you would mount the window partition and then go to the ubuntu directory..

if the info from root.disk were sorted by chkdk they should be found in a hidden directory possiblly named Found.0000 or some such thing as I understand it ..

---

