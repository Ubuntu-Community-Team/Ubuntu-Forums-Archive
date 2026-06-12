---
title: "How to &quot;Copy&quot; Kernel from livecd or installation"
date: 2009-10-11
forum: General Help
---

### Post by mac666 on 2009-10-11
Hey
Im stuck here in guide telling me to:

Use Live CD to boot your system. After this, you need to copy the kernel image from the bootable disk and delete the existing kernel image. Rename the copied image to the one that boot loader recognizes. If you use LILO (LInux LOader), you should run /sbin/lilo to translate present location of copied image to disk geometry language and write to partition’s boot sector.

I have NO idea how to do this...
I Know how to boot the live cd - but after that im lost?
Anyone? Please help me! :| Im really new to linux..!

---

### Post by mcduck on 2009-10-11
Could you explain what are you trying to do, and perhaps also post a link to the guide you are trying to follow?

---

### Post by mac666 on 2009-10-11
This is the link
[http://www.articlealley.com/article_941641_11.html](http://www.articlealley.com/article_941641_11.html) 

Im trying to get my ubuntu to boot...

Its the first "sulotion" to my problem im referringer to

---

### Post by mcduck on 2009-10-11
If you are getting CRC error on boot you sure have some more serious issue with your filesystem or the hard drive, and that part of the guide doesn't really solve the actual problem. It would only allow you to temporarily get the system running so you could back up your files, but that's easier to do simply by booting with a live-CD anyway.

Like the article tells, there are several reasons why you would get the CRC error:

> Kernel image is stored on bad sectors. When Linux kernel image gets uncompressed, it runs a CRC check to ensure its integrity. If checksum values don’t match, it gives errors, as above.

• Bad hard drive

• Bad hardware components like system memory or CPU cache

• File system issues


Restoring the kernel image from live-CD won't actually solve any of these. Running fsck on the drive might solve the last one (file system issues), the rest are actually hardware problems and the only solution to those is replacing the hardware, in most cases the hard drive.

What I'd recommend is booting with a live-CD, and then running "sudo fsck /dev/sda1" (replace "sda1" with the correct device & partition of course.). If that doesn't solve the problem you should run a SMART check on the drive to make sure it's not dying. You should also run the memory test from Ubuntu's live-CD.

Before all those are done replacing the kernel image would be just a waste of time since any hardware problem that might have corrupted your kernel now would just do it again, and in worst case actually corrupt your personal files..

(Besides, the Live-CD most likely doesn't have the same kernel version you were using anyway, so doing what that article suggests would just break a lot of things..)

---

### Post by mac666 on 2009-10-11
Well,
The fsck doesnt do it
Tried and i tried
It just give me that its "good"...
And its not the hardware, since im running all the other OS fine on the same drive and setup..!:confused:

---

