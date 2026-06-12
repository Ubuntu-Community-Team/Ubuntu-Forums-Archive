---
title: "Converting free space to Linux partition"
date: 2010-07-10
forum: General Help
---

### Post by search66 on 2010-07-10
I'm dual booting Win7 with Ubuntu 10... I just 'shrunk' some disk space in my NTFS partition (about 60gb); and want to assign it to my current Linux partition.  In the 'disk utility', I see 60gb 'free' and unformatted.

How can I take this 60gb and add it to my current Linux partition (/dev/sda5)?  Thanks for the help!!!

---

### Post by 23dornot23d on 2010-07-10
Can you show a screen shot ..... of the partition usiing gparted

sudo gparted

take a screenshot using ksnapshot

and then leave gparted

post the picture of it on here if you could ...... 

(imageshack or tinypic are ok for screenshots I find 800 x 600 pixels is a good size too just add a link to it)

I just want to see how the disk you are using is layed out at the moment .........

---

### Post by search66 on 2010-07-10
Here is the SS.. and thanks!

---

### Post by 23dornot23d on 2010-07-10
Ok that looks nice and easy ..... you should be able to pick the linux partition 

Using gparted and resize ....... 

Drag it to the left - so dragging the arrow ..... on the left side ..... on the partition to the right of the free space ....

Once you have committed to doing this change leave it till it completes it will take a long time as it will
re-size and then move all of the data in your linux partition to the left ....... depending on your computer
and how much DATA is there it could take a while ...... (sometimes an hour or more)

**Make sure you have backed up any important DATA first though ......**
[COLOR=Red](I have never had a problem doing this - but its best safe than sorry)



[/COLOR]

---

### Post by search66 on 2010-07-10
I know I'm a bit noobish, so I'm still learning... However, I'm assuming my main Linux partition is /dev/sda5 (ext4)... When I right click on it; the resize is grey'ed out... Do I need to unmount first?

---

### Post by 23dornot23d on 2010-07-10
Yes you need to unmount ...... 
(But you will be using sda5 if you are in Linux ....on that drive)

[B]So my advice is to boot from a UBUNTU 10.04 Linux CD and do it from that ..........
[/B] Just check and make sure the gparted version ..... is 0.5.1 or above .
( I would download the later version of gparted when running the CD .... to be safer )

I seem to remember reading not so long ago about a [re-size problem with older versions]("http://gparted-forum.surf4.info/viewtopic.php?id=13960")

Ok ... the versions of Gparted shown to be problematic in the article above .... are below 0.5.1

The latest version I am using is 0.5.2 .....

you can check the version by opening gparted going to the right menu and clicking About ..... it gives the version

Its a simple enough operation once you have the Latest gparted ..... rather be safe than sorry with things like this.

**But do backup important information when altering disk partition sizes**

---

