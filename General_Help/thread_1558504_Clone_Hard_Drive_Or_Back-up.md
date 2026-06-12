---
title: "Clone Hard Drive? Or Back-up?"
date: 2010-08-22
forum: General Help
---

### Post by ve2 on 2010-08-22
I want to easily clone a hard drive (WinXP) via Ubuntu 10.04. Is there an easy way?

I would also like to back-up my Ubuntu hard drive. Is there such a program to easily clone the Ubuntu drive.

I don't want to buy Acronis or any other product... I am seeking a FREE method via Ubuntu.

---

### Post by listerdl on 2010-08-22
have a look at [http://www.partition-tool.com/](http://www.partition-tool.com/)

you might want to compare that.

clonezilla is also the most recognised by this forum in my opinion.

---

### Post by john newbuntu on 2010-08-22
Take a look:
[http://www.youtube.com/watch?v=7nHur5BvV6o](http://www.youtube.com/watch?v=7nHur5BvV6o)

Credits to Youtube and the folks at JupiterBroadcasting for this overview.

---

### Post by ve2 on 2010-08-22
I will check these out. I did try a simple copy and paste to another folder. That was funny.. after the format of the windows drive and then a copy and paste back to the windows drive form the saved folder in Ubuntu.. I got C drive corrupt and 2 desktop.ini files popping up on Windows start-up... not a good idea.. will look at the other suggestions.

---

### Post by aysiu on 2010-08-22
CloneZilla's definitely the way to go. Works for Windows. Works for Linux. Works for a combined Windows and Linux dual-boot. The best part is that during the cloning process, it copies only the amount of hard drive space being used. So if you have a 250 GB hard drive with only 40 GB of it used, the cloned image size will be about 40 GB, not 250 GB.

---

### Post by coffeecat on 2010-08-22
> **ve2 said:**
> I don't want to buy Acronis or any other product... I am seeking a FREE method via Ubuntu.

You can use the dd command in Ubuntu to copy a Windows drive but if you want to do something that will be completed before the turn of the next millennium, you really need good imaging software like Acronis. And there is one that's free.

[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)

It's proprietary but free, and reasonably quick. I've used it to backup and restore XP, Vista and Windows7. To restore, once you have an image on a USB drive or whatever, you use the rescue CD which you make with the main app. The rescue CD is Linux-based, so that can't be bad!

Of course, that's for your Windows installation only. For Ubuntu, go with the other suggestions.

---

### Post by aysiu on 2010-08-22
> **coffeecat said:**
> 
It's proprietary but free, and reasonably quick. > Of course, that's for your Windows installation only. For Ubuntu, go with the other suggestions. These are two good reasons I recommend CloneZilla. It's both free and open source, and reasonably quick; and it can back up and restore *both* Windows and Ubuntu.

We actually use CloneZilla at work to multicast our Windows 7 images to staff, faculty, and students (twenty at a time).

---

### Post by coffeecat on 2010-08-22
> **aysiu said:**
> These are two good reasons I recommend CloneZilla. It's both free and open source, and reasonably quick; and it can back up and restore *both* Windows and Ubuntu.

We actually use CloneZilla at work to multicast our Windows 7 images to staff, faculty, and students (twenty at a time).

Good point. I can see the advantage of Clonezilla. I don't use it myself because I use tar to backup/clone my Linux installations. It's quick, simple and effective but I didn't mention it because whenever I do someone usually chips in and complicates things by saying you have to use a load of excludes for the virtual directories. You don't, but I haven't got the energy to argue the point. :wink: And that's how I came across Macrium.

But I will have another look at Clonezilla. It'll get me out of a rut, if nothing else. Thanks.

---

### Post by aysiu on 2010-08-22
> **coffeecat said:**
> 
But I will have another look at Clonezilla. It'll get me out of a rut, if nothing else. Thanks. Well, the major downside to CloneZilla is the interface is not particularly user-friendly and pretty. If you read things carefully, it works extremely well, though... and that's for cloning one drive. If, however, you want to do a multicast clone, even reading carefully won't have things make sense to you necessarily.

---

### Post by ve2 on 2010-08-22
Is there a demo of how to install CloneZilla? And all the others seem good also. I have seen the Acronis software, but I need a FREE option - I really want to go on the trail of OPEN source. If there is a CloneZilla install method for Ubuntu.. Pls share!

---

### Post by ve2 on 2010-08-22
I like the FREE idea - I will check this out. I wonder if I can run Windows in Virtual Box and then back up my REAL WInXP drive.. without having to install this proggie on my FRESH windows install.

---

### Post by ve2 on 2010-08-22
> **aysiu said:**
> Well, the major downside to CloneZilla is the interface is not particularly user-friendly and pretty. If you read things carefully, it works extremely well, though... and that's for cloning one drive. If, however, you want to do a multicast clone, even reading carefully won't have things make sense to you necessarily.

> **ve2 said:**
> I like the FREE idea - I will check this out. I wonder if I can run Windows in Virtual Box and then back up my REAL WInXP drive.. without having to install this proggie on my FRESH windows install.

> **listerdl said:**
> have a look at [http://www.partition-tool.com/](http://www.partition-tool.com/)

you might want to compare that.

clonezilla is also the most recognised by this forum in my opinion.


How does [http://www.partition-tool.com/](http://www.partition-tool.com/) compare to Clonezilla.. Can it only back what I need or will it back-up the entire drive? I have a 1TB drive.. I only want to back-up the portion used.

---

### Post by ve2 on 2010-08-23
[john newbuntu]("http://ubuntuforums.org/member.php?u=956991") Wrote: Take a look:
[http://www.youtube.com/watch?v=7nHur5BvV6o](http://www.youtube.com/watch?v=7nHur5BvV6o)

GOOD Video... gave me a real good idea!

---

