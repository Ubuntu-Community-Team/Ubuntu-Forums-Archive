---
title: "Adding unallocated space to my Ubuntu Partition in gparted"
date: 2011-01-09
forum: General Help
---

### Post by Dangerzone812 on 2011-01-09
Hey all, I have a question, I have two partitions on my computer, one for Windows, and one for Linux. WELL, I want to transfer the like 50 gigs of extra space from window's to Linux.

Now I know I need to use gparted, and I already shrunk my Window's partition, so now I have all this unallocated memory that I want to give to Linux....but can't. :\ Help?

Thanks in advance,

Danger.

---

### Post by TeoBigusGeekus on 2011-01-09
Try moving the unallocated space next to the partition you want to grow.

---

### Post by Dangerzone812 on 2011-01-09
How do I go about and move it? 

I mean it's right next to each other, like this:

{[Windows 7 Partition] [Free space] [(Ubuntu) (Some free space on that partition)] [Windows recovery]}

If that chart makes sense:

{} - Whole hard drive:
[] - Partitions
() - subsections of each partition

---

### Post by srs5694 on 2011-01-10
Please post either a screen shot of GParted or the text-mode output of "sudo fdisk -lu" between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings.

---

### Post by Bucky Ball on 2011-01-10
Hold on. ONE MAJOR ISSUE! You can do this easily without fuss. You are virtually there but missing one essential element and surprised no-one picked it up. There are **two** partitions on the machine; one Windows and one Ubuntu. **_*OP is attempting to resize the partition which is running gparted and the OS. *_**

Your Ubuntu partition needs to be unmounted to do what you want to do. Therefore, you are going to need to boot from the LiveCD and run Gparted from the desktop there. ALL partitions are/can then be unmounted. Once unmounted just right click the Ubuntu partition, click resize, and drag the slider over the unallocated space, doesn't matter if in front or behind, as long as it's next to your Ubuntu partition. That easy.

You've done the hard part resizing Windows.

You can't unmount the Ubuntu partition if you are running Ubuntu on it (and Gparted). Get the picture? ;)

---

### Post by Dangerzone812 on 2011-01-11
I think I understand what you mean Bucky Ball. I just don't know how to unmount it. More detailed instructions?

This is also a screen shot from my gparted:

[http://sphotos.ak.fbcdn.net/hphotos-ak-snc4/hs1366.snc4/163878_1738294944499_1452400637_1806551_7477385_n.jpg](http://sphotos.ak.fbcdn.net/hphotos-ak-snc4/hs1366.snc4/163878_1738294944499_1452400637_1806551_7477385_n.jpg)

---

### Post by Bucky Ball on 2011-01-11
Boot from a liveCD, get to the desktop. Right click on the partitions there if you like and 'Unmount' or open gparted and right click the partition you want to work on and 'unmount'. Then you're good to go.

---

### Post by Dangerzone812 on 2011-01-11
I'm currently trying it right now, and it doesn't have the option to unmount. D:

---

### Post by Dangerzone812 on 2011-01-11
In reference to this picture:

[http://sphotos.ak.fbcdn.net/hphotos-ak-snc4/hs1366.snc4/163878_1738294944499_1452400637_1806551_7477385_n.jpg](http://sphotos.ak.fbcdn.net/hphotos-ak-snc4/hs1366.snc4/163878_1738294944499_1452400637_1806551_7477385_n.jpg)

I need to move /dev/sda5 in between /dev/sda1 and the unallocated memory to expand it into the unallocated memory.

---

### Post by Quackers on 2011-01-11
So you want to extend your Ubuntu partition (sda5) to use the unallocated space which is now just after sda1, is that correct?
If so, as sda5 is within an extended partition (sda2) you must first extend sda2 in to the unallocated space. This will take a few seconds, I believe.
Once that is done, you can extend sda5 into that space, which will then be "free space" within sda2. This will not take a few seconds! More like two and a half hours, maybe.

---

### Post by srs5694 on 2011-01-11
You need to do as Bucky Ball suggested and boot from a live CD. You should be able to use an Ubuntu installer's live CD mode, or you can try [System Rescue CD](http://www.sysresccd.org) or [Parted Magic.](http://partedmagic.com)

---

### Post by Dangerzone812 on 2011-01-11
I'm in gparted right now, tryin to extend sda2....but when I right click, my only options are "Manage Flags" and "Information".:(

---

### Post by Dangerzone812 on 2011-01-11
Well, right now, I'm currently trying to extend my sda2 into the unallocated space, so I can give it to sda5...but the only options when I right click sda2 are "Manage Flags" and "Information"

---

### Post by Quackers on 2011-01-11
Sorry, I should have mentioned, it is not wise to do this from within a mounted system.
You should use the live cd/usb version of gparted. The first job is to right-click on the swap partition and select "swapoff". Then each job can be done individually, clicking on the green tick mark in the toolbar after each stage.
Then at the end right-click on the swap partition and select "swapon" again.

---

### Post by lithopsian on 2011-01-11
This would require you to extend sda5 "backwards".  Not possible, I thought?

---

### Post by Quackers on 2011-01-11
It is possible to extend "to the left", partitions are not stuck in concrete :-) but it is necessary that the unallocated space is next to the partiton to be extended.

---

### Post by RJ12 on 2011-01-11
Are you in the live cd?

---

### Post by Bucky Ball on 2011-01-11
> **rj12 said:**
> are you in the live cd?

+1. ???

---

### Post by Quackers on 2011-01-11
The OP has 2 threads on the same subject. I have asked a Mod to merge them.

And like magic - it's done :-)  Thank you Mr Moderator!

---

### Post by uRock on 2011-01-11
Merged related threads.

---

### Post by Dangerzone812 on 2011-01-11
> **Quackers said:**
> Sorry, I should have mentioned, it is not wise to do this from within a mounted system.
You should use the live cd/usb version of gparted. The first job is to right-click on the swap partition and select "swapoff". Then each job can be done individually, clicking on the green tick mark in the toolbar after each stage.
Then at the end right-click on the swap partition and select "swapon" again.


Your directions worked flawlessly! Thanks SO much!

---

### Post by Dangerzone812 on 2011-01-11
> **Quackers said:**
> Sorry, I should have mentioned, it is not wise to do this from within a mounted system.
You should use the live cd/usb version of gparted. The first job is to right-click on the swap partition and select "swapoff". Then each job can be done individually, clicking on the green tick mark in the toolbar after each stage.
Then at the end right-click on the swap partition and select "swapon" again.


Your directions worked flawlessly! Thanks SO much! 


Case closed!

---

### Post by Quackers on 2011-01-11
Excellent :-)
You're welcome.
Can you mark the thread as solved using the Thread Tools near the top of the page? Thanks.

---

### Post by Bucky Ball on 2011-01-11
Good news! 

Please mark thread as 'solved' from 'Thread Tools', top right.

* LOL Quackers, you beat me to it. Snap!

---

### Post by Quackers on 2011-01-11
Indeed :-) Mr Bucky Ball, Bathed in 'Buntu, do you like B's :-)

---

### Post by Bucky Ball on 2011-01-11
> **Quackers said:**
> Indeed :-) Mr Bucky Ball, Bathed in 'Buntu, do you like B's :-)

Not as much as butterflies! lol

It was going to be 'Bathed in a bath of 'Buntu' but I thought that was going *too* far! ;)

---

### Post by Quackers on 2011-01-11
> **Bucky Ball said:**
> Not as much as butterflies! lol

It was going to be 'Bathed in a bath of 'Buntu' but I thought that was going to far! ;)

Lol, it should have been Bathed in Bees :-)

---

