---
title: "How to change partition name / identity? - gparted"
date: 2009-12-28
forum: General Help
---

### Post by tedrogers on 2009-12-28
Hi all,

So let me explain, I used to have 4 partitions on 1 disk, simply as follows:

/dev/sda1 - /
/dev/sda2 - /home
/dev/sda3 - swap
/dev/sda4 - [general backup space]

I just got a USB hard drive and now use this as my backup space (/dev/sda4), so in order to make my /home (sda2) partition larger I used gparted to delete the backup space (sda4), move the swap space (sda3) to the end of the disk and 'grew' the home (sda2) directory to fill up the remaining space. It all worked brilliantly and Ubuntu still recognises my /home directory. 

But...not sure how this happened, but sda2 is now called sda4 (which was my old general backup space that I deleted).

My partitions now look like this:

/dev/sda1 - /
/dev/sda4 - /home
/dev/sda3 - swap

...sda2 is now missing.

Really what I would like is this:

/dev/sda1 - /
/dev/sda2 - swap
/dev/sda3 - /home

So how can I do this?

I know I could move the swap space in gparted to the place where I want it, but how do I rename the partitions and how do I make sure that Ubuntu isn't borked and that everything works as it does now, but with a nicely ordered set of partitions?

Onward in my quest to understand Linux I go...but need help from you good people! :)

Thanks all.

---

### Post by jman6495 on 2009-12-28
> **tedrogers said:**
> Hi all,

So let me explain, I used to have 4 partitions on 1 disk, simply as follows:

/dev/sda1 - /
/dev/sda2 - /home
/dev/sda3 - swap
/dev/sda4 - [general backup space]

I just got a USB hard drive and now use this as my backup space (/dev/sda4), so in order to make my /home (sda2) partition larger I used gparted to delete the backup space (sda4), move the swap space (sda3) to the end of the disk and 'grew' the home (sda2) directory to fill up the remaining space. It all worked brilliantly and Ubuntu still recognises my /home directory. 

But...not sure how this happened, but sda2 is now called sda4 (which was my old general backup space that I deleted).

My partitions now look like this:

/dev/sda1 - /
/dev/sda4 - /home
/dev/sda3 - swap

...sda2 is now missing.

Really what I would like is this:

/dev/sda1 - /
/dev/sda2 - swap
/dev/sda3 - /home

So how can I do this?

I know I could move the swap space in gparted to the place where I want it, but how do I rename the partitions and how do I make sure that Ubuntu isn't borked and that everything works as it does now, but with a nicely ordered set of partitions?

Onward in my quest to understand Linux I go...but need help from you good people! :)

Thanks all.

wow , that's a little picky!
mine have done that too , also looking for a solution

---

### Post by louieb on 2009-12-28
lol -clearly a case of if it ain't broke - tweak it till it is. 

anyway an ms-dos partition table has 4 entries. the 1st - sda1 ... 4th ... sda4. 

You can use sfdisk or fdisk to rearrange your partition table entries. Sfdisk might be a little easier. [sfdisk to fix partition table problems]("http://ubuntuforums.org/showthread.php?t=1192598")

---

### Post by tedrogers on 2009-12-29
> **louieb said:**
> lol -clearly a case of if it ain't broke - tweak it till it is. 

anyway an ms-dos partition table has 4 entries. the 1st - sda1 ... 4th ... sda4. 

You can use sfdisk or fdisk to rearrange your partition table entries. Sfdisk might be a little easier. [sfdisk to fix partition table problems]("http://ubuntuforums.org/showthread.php?t=1192598")

:P Haha yes definitely guys...I'm crazy like that. It must be a form of OCD.

I will try out your suggestions and no doubt let you know when it's all a complete mess! :lolflag:

---

### Post by DShad on 2010-02-12
I need help please...

I managed to find the PT.txt I have.  Here it is:

# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=        0, size=        0, Id= 0
/dev/sda2 : start=       63, size=1929743802, Id=83
/dev/sda3 : start=1929743865, size= 23776200, Id= f
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=1929743928, size= 23776137, Id=82


I want to get rid of the sda1 & sda4 so I can only have something like:
/dev/sda1 : start=       63, size=1929743802, Id=83
/dev/sda2 : start=1929743865, size= 23776200, Id= f
/dev/sda3 : start=1929743928, size= 23776137, Id=82

Can I just do that (as above) and put it back as my new PT.txt?

Thanks for your help.

---

### Post by tedrogers on 2010-02-12
I was really led by the advice of the other guys on here...sorry but I'll be about as much use as a chocolate tea pot to you.

---

### Post by bruno9779 on 2010-02-12
You are forgetting to put an important detail into the picture.
Are the partitions primary , extended or what?

I have sda1, sda2, sda6, sda7, sda5, sda3.
But s you can see from the screenshot, sda5 sda6 sda7 are sub-partitions of sda2, so they are more or less in order.

[[img]http://www.ubuntu-pics.de/thumb/42400/screenshot_010_4EW58n.png[/img]](http://www.ubuntu-pics.de/bild/42400/screenshot_010_4EW58n.png)

---

### Post by DShad on 2010-02-12
> **bruno9779 said:**
> You are forgetting to put an important detail into the picture.
Are the partitions primary , extended or what?

I have sda1, sda2, sda6, sda7, sda5, sda3.
But s you can see from the screenshot, sda5 sda6 sda7 are sub-partitions of sda2, so they are more or less in order.

[[img]http://www.ubuntu-pics.de/thumb/42400/screenshot_010_4EW58n.png[/img]](http://www.ubuntu-pics.de/bild/42400/screenshot_010_4EW58n.png)

What I have is:

sda2 primary ext4
sda3 primary extended
 |  
 ---sda4 linux swap

Here's the screenshot!

Thanks

---

