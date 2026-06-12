---
title: "Resizing partitions"
date: 2010-11-03
forum: General Help
---

### Post by Fracta on 2010-11-03
I just did a search and couldn't find anything that would be of use to me.
I want to shrink a partition on an external HD. Doesn't have OS on it or anything. All the threads I could find were about resizing OS partitions.
I checked in the Disk Utility, but couldn't see anything about resizing.
I want to shrink the partition on my 1.5 TB hard drive (most of it is empty) so that I can use ddrescue to rip an image and see if I can rescue some more of my files. At the moment, I don't have anything big enough to store a 1.5 tera image. I realise there is a risk with doing this, but I have managed to rescue at least half of my files and most of them are the important ones.
I have tried setting ddrescue to only rip a certain amount (like a 400GB image) but it won't mount, and I assume this is because the partition tables aren't updated for 400gb.
Any ideas?

---

### Post by sikander3786 on 2010-11-03
I would use gparted for that. Instructions here.

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

---

### Post by Fracta on 2010-11-04
Ok, got gparted, but its not letting me resize the partition. I try to drag the arrows and manually type in the new size but it won't let me. The arrows are stuck and whenever I type a size in, it gets erased whenever I click anything else.
Also, what do the icons next to the drive mean? Like in this case, there is an exclamation mark, where usually there is a key (in the screenshot). Where are the explanations for the icons?
And do you know what the problem is?

---

### Post by P4man on 2010-11-04
edit: ignore. Im wrong, its ntfs.
As the below poster said, it doesnt work when its mounted, right click and unmount. 
If that doesnt help its probably that the filesystem needs checking, boot windows and run chkdsk /F

---

### Post by arapaho on 2010-11-04
Gparted doesn't work on mounted partitions. Try boot from gparted LivCd. Read about ntfs, FAQ point 16:
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

---

### Post by efflandt on 2010-11-04
That red exclamation point means that something is wrong or missing.  If you right click on that partition in gparted and click on **Information**, what does that tell you?

Normally if a partition is mounted, it would have a key by it meaning it is locked.  But in the case of exclamation point in yellow triangle or red circle, there is some other reason that gparted does not want to do anything with it.

The only way I can duplicate a red ! on my system is by looking at a drive that has been zeroed with no partition table.  So gparted Information in that case tells me **! Warning: /dev/hdb unrecognized disk label**.  Or if I click on the icon for new partition, it tells me: **No partition table found on /dev/hdb** A partition table is required before partitions can be added...

It is possible that the drive was not safely removed (possibly writing while mounted).  Are you able to connect the drive to a Windows PC, have it recognized as a drive letter, and run chkdsk /f on that drive letter?

That was good enough to fix a laptop boot drive with bad sectors (boss' grandson) from a USB enclosure, so I could image it with Acronis (clonezilla would not work with bad sectors) for the warranty replacement drive.  And chkdsk /f likewise fixed the warranty replacement drive that was later corrupted by a Windows virus, so I could virus scan it from another PC.  Then they broke the laptop screen, oh well.

---

### Post by Fracta on 2010-11-04
Yeah I realise you wouldn't be able to resize a partition if it was mounted. However, its only when it is mounted that I can see how much space is being used and how much to shrink it by. 
It is ntfs. Windows REALLY doesn't like it. Treats it as an unformatted disk. Also, I spent about 20^6 hours trying to get the dam thing fixed with windows (I even used acronis), and after using at least 5 different recovery programs and tons of forums etc, I still had 0 bytes recovered, but I did manage to see that all the folders were still on the drive.

I plug it into Ubuntu, and in 2 minutes I'm transferring over files.  However, not all the files want to copy over. Some stop half way, and there are a few folders that are just empty. 

It is a little unusual I think to have an external formatted as ntfs, am I right? Every other one I have seen is fat32. The < 4gb file size limit really ticked me off sometimes. 

I am pretty sure that someone unplugged my hard drive at the wrong time or something and caused all the damage. This would be almost 6 months ago. I am still a student/minimum wage worker so I can't afford +300 for freakin repairs. I have to learn everything myself. 

To cut a long story short, I don't see why I should be forced to use windows. There must be a linux chkdsk I can use (I'm sure I remember seeing the option in gparted), but the whole point was to just cut out the empty space and rescue the whole drive without doing any repairs or anything that might erase my files. 
Windows didn't help at all, and it leaves a bad taste in my mouth. I would prefer to just use linux apps and avoid having to reboot etc, also I have tried windows chkdsk and it freezes half way.

P.S. sorry for long post, and thanks for the replies!

---

### Post by P4man on 2010-11-04
To fix ntfs problems, your best bet really is windows. If windows cant fix it, dont even try under linux. What you can try under linux is recover data. Id recommend you install testdisk and run that or photorec (same suite) to recover as much as possible. Testdisk is in the repository I think. Excellent tutorials available on their site:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

You can run it from a livecd too if you need.

What you certainly do NOT want to do ever is doing something like shrinking a damaged partition. That is just going to make the problem exponentially worse.

Anyway, good luck getting your data back.

---

### Post by P4man on 2010-11-04
afterthought: its possible that the problem is caused by or related to the external drive enclosure/controller. You could try opening it and putting the drive in your desktop. These things contain regular sata drives.

---

### Post by Fracta on 2010-11-04
Yeah I actually bought the enclosure and the HD separately. But I don't think its an enclosure problem. Otherwise, how would I be able to rescue half my data?
I might try it if testdisk doesn't work.

---

### Post by P4man on 2010-11-04
Maybe the enclosure's controller doesnt support drives larger than 1TB? Its not quite the same thing, but I have a card reader that doesnt support memory cards larger than 2GB. If I plug in a 4+GB card, I can still read and write to it..  ubuntu sees it as 4GB card,  I can read only anything "below" 2 GB and if I copy files, once I exceed 2GB, I get IO errors. Card itself is fine. Card reader too with smaller cards.

Anyway, just a thought.

---

### Post by Fracta on 2010-11-04
Still looks like my best option is rip an image and work with that. I just had a flick through the testdisk site. I won't get to try anything til I get back from work in a few hours anyway. I just ordered a 2 TB external so that I have space to copy image to. Thats going to take *days*. 
I have read about the various linux filesystems, but couldn't really figure out which was best. Should I just format the external as ext3?

---

### Post by alphaamanitin on 2010-11-04
Before you do anything else you should look into cloning the drive.  But read up on your possible errors first.  I have read that checking drives with certain errors can actually damage your drive more and decrease your chances of successful data recovery.  Also, I think using dd to clone a drive with I/O errors is dangerous, but I may not remember correctly.

AlphaA

---

### Post by P4man on 2010-11-04
> **Fracta said:**
> Still looks like my best option is rip an image and work with that.

Not if the USB controller doesnt let you read beyond 1TB (or 500GB or whatever), which, the more I think about it, the more I think could actually be the case and the root cause of your problem. It would also explain why windows cant do a damn thing about it and doesnt seem to achieve anything.

> I have read about the various linux filesystems, but couldn't really figure out which was best. Should I just format the external as ext3?


Ext4 would be my choice.

---

### Post by onaridge on 2010-11-04
"It is a little unusual I think to have an external formatted as ntfs, am I right? Every other one I have seen is fat32. The < 4gb file size limit really ticked me off sometimes." 

I think newer externals are coming formatted with NTFS now because I have been shopping for some and they were all NTFS. I know with Windows 7 you can't use their image backup utility onto an external unless it is NTFS.

---

### Post by Fracta on 2010-11-05
I'm not sure if that is possible. I had already copied over 400GB onto the drive before it stopped being recognized by windows. Its not too much of an issue to take out the drive and stick it in my pc.
How can I check to make sure the usb controller can read beyond 1tb? I'm sure my brothers external is 1.5 tera and we have never had a problem. His one is a western digital I think so he didn't make it up from components like i did.

I was wondering if I shouldn't have formatted the drive as ntfs (because I have large isos that need to fit) but if newer ones are coming out with it, I guess its not the problem.

---

