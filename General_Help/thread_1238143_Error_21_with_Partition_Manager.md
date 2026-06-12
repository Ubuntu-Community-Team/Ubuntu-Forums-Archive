---
title: "Error 21 with Partition Manager"
date: 2009-08-12
forum: General Help
---

### Post by Mr_Lazy on 2009-08-12
Hi,

I am running Ubuntu 8.04 WUBI and I want to go to a full Ubuntu install. 

I need to create a new partition but I am currently having an issue with Partition Manager. When I reboot after installing the package, pressing Esc to get into the menu, select the partition manager, I get the error:

> Booting 'UNetbootin-partitionmanagerrev146'
root (hd1,)

Error 21: Selected disk does not exist 

I am kind of stuck here. I found a post by someone who said their problem was solved, but they did not say how they solved it.

[http://ubuntuforums.org/showthread.php?p=6057831](http://ubuntuforums.org/showthread.php?p=6057831)

I think I need a bit of hand holding to solve this problem....

Many Thanks,
Stephen

---

### Post by P4man on 2009-08-12
When you say partition manager, are you sure you don't mean 'grub bootloader' instead?

Im slightly confused as to what is going on, but maybe thats because I never used wubi. Can you elaborate a bit how you got where you are now? What did you do exactly?

---

### Post by Mr_Lazy on 2009-08-12
Hi,

I have been using Wubi 8.04 for several months now, and I want to install a full install of 8.04. Using this guide:

[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

I am at the first stage. I have downloaded the "Partition Manager for Ubuntu" and installed it. Rebooted, at the boot menu selected Ubuntu, then I pressed Esc to get to the menu where I am able to select the partition manager. It is then at this point I get the error:

> Booting 'UNetbootin-partitionmanagerrev146'
root (hd1,)

Error 21: Selected disk does not exist 

Hope that clarifies my problem for you.

Stephen

---

### Post by P4man on 2009-08-12
yeah that explains a lot :)

Ive never used any of that, but I understand what they are trying to do. That bootable partition manager looks neat if it would work, but it doesnt :) 

We could try fixing the partition manager grub entry, but its probably just as easy you prepare your partitions with a live cd. Boot from the livecd, then run partition editor from there to make your new partition just like in that tutorial. Then reboot and proceed with the rest of the instructions.

That is, if this step is required at all. Are you installing on to a new harddisk ?

---

### Post by Mr_Lazy on 2009-08-12
No, I am installing on an existing disk (Windows XP and all). Thanks for the suggestion of the Live CD, I'll give that a try.

---

### Post by Mr_Lazy on 2009-08-12
Well, that did not go very well. I don't have the 8.04 CD around here (or any blanks), so I used an old 7.10. Not surprising, this did not work, there must be another way.

I would consider a clean install, but I am going to lose all my settings, links etc, it will take me ages to get everything back to normal. This a laptop I do work on so this is an issue.

Any other ideas?

Thanks,
Stephen

---

### Post by P4man on 2009-08-12
what didn't work? A 7.10 cd would be good enough to launch gparted (partition editor) and make your partitions I'd think. Can't it read and resize ntfs partitions, or what is the problem? You can find the partition editor in system > administration menu of the livecd.

Im not sure how confident you are in what you're about to do though. Do you know how to create, resize partitions? You have a basic understanding of that?

Whatever you do, do make a backup of your important stuff first.

---

### Post by Mr_Lazy on 2009-08-12
Right, I think I got the wrong end of the stick. I thought you suggested I try to run the partition manager, but I mis-read, you said the partition **editor.**

I'll try again. Is the idea that as you are running from a CD, you can change/create a partition because you are not running the OS on the hard drive?

I have dabbled in partitioning hard drives before (for a ASUS eee) but that was a while ago.

All data backed up. Here we go....

---

### Post by Mr_Lazy on 2009-08-12
Hi,

Using GParted via the 7.10 Live CD, I tried to shrink the main partition, and add two more. One swap partition of about 3.7GB and one main partition of about 40GB.

GParted crashed. Error Reported

> gparted crashed with SIGSEGV in std::basic_string()

I will try again...

---

### Post by P4man on 2009-08-12
[https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/136485](https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/136485)

2 year old bug :) but it only seems a problem if the windows volume wasnt closed properly. Try booting windows, shut it down properly, then try again.

---

### Post by Mr_Lazy on 2009-08-12
I can't get this to work, GParted just crashes when it tries to shrink the main partition.

I have tried to save the crash report (in root) but then I can't find it to reproduce here.

---

### Post by P4man on 2009-08-12
well, like I wrote up, its an old bug.. If booting/shutting down windows doesn't work, Id suggest downloading a newer live cd.

Or you could try updating gparted on your current.

Not 100% sure if this will work, but try:

```
sudo aptitude reinstall gparted
```

while in the live session.
Im hoping that will fetch a newer (less buggy) version.

---

### Post by Mr_Lazy on 2009-08-12
Unfortunately that (edit: closing windows properly) did not work. :confused:

I am seriously thinking about abandoning this, getting a blank CD, burning the latest Ubuntu onto it and starting again with a complete install. This seems very fiddly and fraught with dead ends...

---

### Post by P4man on 2009-08-12
thats one option of course :)
Although what we're trying to achieve here, is only make a partition... that's supposed to be the easy part :)

Im not sure what version of windows your have, but maybe you can do it in windows ? If windows can't do it by default (I think vista and upwards can resize their own partition, but im not sure), then get something like partition magic. 

Or a newer copy of ubuntu :p

---

### Post by Mr_Lazy on 2009-08-12
I'm running Windows XP Professional. I will try some more things tomorrow... like running a newer Live CD and try gparted from there. If that does not work I'll get out the sledgehammer out to crack the nut and do a clean install.

Thanks for your time and patience.

---

### Post by raymondh on 2009-08-12
> **Mr_Lazy said:**
> I'm running Windows XP Professional. I will try some more things tomorrow... like running a newer Live CD and try gparted from there. If that does not work I'll get out the sledgehammer out to crack the nut and do a clean install.

Thanks for your time and patience.

Just some thoughts:

1.  I normally use windows programs to work on windows partitions but I don't think XP's disk manager can/will shrink.  That said, I would try to download, burn to disc and use the latest version of [gparted]("http://gparted.sourceforge.net/download.php").  Good disc to have as part of your 'tools'. 
2.  Defrag XP
3.  Your WUBI install, was it 8.04 based?  If so ... and it worked for you .... I would consider installing 8.04 LTS again.  Of course, you could always try in liveCD the newer jaunty to see if it works and then install.
4.  As you prepare to partition and dual-boot, consider separating your /home from root (/) .... that way, should you need to re-install in the future, you can still retain your current config settings and files.

You mentioned that "it's been a while since you've done partitioning".  Some links for reference:

[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)
[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[http://members.iinet.net/%7Eherman546/index.html](http://members.iinet.net/%7Eherman546/index.html)
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Separate /home (as you know) can be created as you install or after you install.  Post back if you need assistance in manual installations.

Good luck.

---

### Post by Mr_Lazy on 2009-08-13
@Raymond

You posted probably the most useful post I have ever had written to me on a forum. From your list of suggestions I went straight to:

> 2. Defrag XP

I set the thing running overnight, came in this morning and GParted worked first time. Excellent. Then I ran LVPM to copy all my stuff in the WUBI install over to my newly created partition. Problem free. 

My next step is to delete the windows partition and then separate out the root and home partitions. But from the great links you posted it doesn't look too hard to do this.

Any advice where I should have my three partitions (swap, home, root)? From left to right in GParted I mean.

Thanks again,
Stephen

---

### Post by raymondh on 2009-08-13
> **Mr_Lazy said:**
> @Raymond

You posted probably the most useful post I have ever had written to me on a forum. From your list of suggestions I went straight to:



I set the thing running overnight, came in this morning and GParted worked first time. Excellent. Then I ran LVPM to copy all my stuff in the WUBI install over to my newly created partition. Problem free. 

My next step is to delete the windows partition and then separate out the root and home partitions. But from the great links you posted it doesn't look too hard to do this.

Any advice where I should have my three partitions (swap, home, root)? From left to right in GParted I mean.

Thanks again,
Stephen

Stephen,

Excellent news.  Well done :)

My HD order is root (/), /home and then swap. I choose to have swap at the end because modern computers usually have the RAM and HD power.  My current sizings are 8-15GB for root. For swap, I use 1.5GB (note I have 4GB RAM).  The rest for /home.

Swap size is dependent on your requirements.

Happy Ubuntu-ing.


Raymond

---

