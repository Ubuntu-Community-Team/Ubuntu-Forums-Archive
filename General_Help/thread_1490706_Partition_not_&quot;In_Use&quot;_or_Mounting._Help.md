---
title: "Partition not &quot;In Use&quot; or Mounting. Help! Please?"
date: 2010-05-22
forum: General Help
---

### Post by AJchang on 2010-05-22
Hey guys! First of all, I have been in heaven since switching from FreeNAS to Ubuntu Server w/mdadm, Webmin and Deluge. It was not easy, but fortunately there are plenty of helpful guides and forum posts online. Eventually, I'll help my friends to do the same.

Here's the situation. After getting back from hockey last night, I tried to access a 1.5TB hard drive located on *mnt/WD15EADS/private* from my laptop. This is what I found.

[http://imgur.com/liTU8.png](http://imgur.com/liTU8.png)

Unlike my RAID 5 device, located on *mnt/WD6401AALS/public*, there are no folders/files showing up at *mnt/WD15EADS/private*. Further, Finder states only *17.11 GB available*, and I'm pretty sure there was more free space than that. I then took a closer look with the Webmin File Manager.

[http://imgur.com/ZgeVO.png](http://imgur.com/ZgeVO.png)

Something was clearly wrong, because the folder icon should be green. 

Exiting the File Manager and looking at the highlighted drive with Webmin, it seems like the one partition is still there though. [http://imgur.com/Qcaie.png](http://imgur.com/Qcaie.png)

But when I selected the partition last night, it said "Not in Use" or something like that. After trying to mount the drive, the following highlighted text is now displayed. [http://imgur.com/mUubv.png](http://imgur.com/mUubv.png)

But I still can't get it to work! [http://imgur.com/PyvF7.png](http://imgur.com/PyvF7.png)

Where I have highlighted text in this next pic, I tried selecting a different *Disk* or *Partition with ID* to no avail. When I accessed this menu last night, I think *Other Device* was originally selected. [http://imgur.com/RqB06.png](http://imgur.com/RqB06.png)

I then tried fsck. 

[http://imgur.com/CljTO.png](http://imgur.com/CljTO.png)
[http://imgur.com/glSJf.png](http://imgur.com/glSJf.png)

And finally, after nothing worked, I went to bed.


Here is some background. On my motherboard, the drive where Ubuntu Server is installed and booted from is located on SATA1. This 1.5TB drive is plugged into SATA3. Previously SATA2 had no drive connected, but on Thursday I bought a new 2.0TB drive which was plugged into SATA2. I think this 1.5TB drive used to be called sdf1, but now it's called sdg1, though I might be mistaken.

I'm sorry if all those pics were not helpful, or if they were annoying, but being so inexperienced, I'm not sure how to accurately relay information without visual aids. If anyone could help me solve this problem, you would forever receive my gratitude, because there is a lot of stuff on that drive that means a lot to me.

---

### Post by AJchang on 2010-05-22
> **AJchang said:**
> Here is some background. On my motherboard, the drive where Ubuntu Server is installed and booted from is located on SATA1. This 1.5TB drive is plugged into SATA3. Previously SATA2 had no drive connected, but on Thursday I bought a new 2.0TB drive which was plugged into SATA2. I think this 1.5TB drive used to be called sdf1, but now it's called sdg1, though I might be mistaken.

I unplugged the new 2.0TB drive and voila, I can access the 1.5TB drive again. Wow.

---

