---
title: "new laptop and want to partition it"
date: 2011-03-29
forum: General Help
---

### Post by ihatetryingtopickaloginna on 2011-03-29
I don't want to make a mess of the partitions like I did on my desktop when I put 8.04 on it, so need some help please. I have a 320g hard drive with win7 on it and a recovery partition for it also. What it came with. I would like to install v10.10 and have a home partition too. So I can upgrade later without losing my stuff. And keep win7 just to try out occasionally. I ran the install cd but didn't understand how to partition it with the install routine. I have a copy of gparted on cd but I haven't tried it yet, so I can use it if need be.

Thanks

---

### Post by mikewhatever on 2011-03-29
Can you post the output of **sudo fdisk -l** or a screenshot of gparted from the Ubuntu Live CD. Just want to make sure there aren't four primary partition there already.

---

### Post by irv on 2011-03-29
I know what you are saying about having your /home on its own partition, but I did mine a little different. I also have Win7 and Ubuntu 10.10 on my laptop and I wanted to be able to get to my files from both OS's. The only way I could do this was to make a NTFS formated partition and put my files there so windows would read it. If I set it to mount /home it would have been formated with Ext3 or 4. Here is a screen shot of my gparted so you can see how I setup my hard drive.
[ATTACH]187472[/ATTACH]
I am not suggesting you do it this way, I am just showing you how I did it. There are different strokes for different folks.
Irv

---

### Post by Megaptera on 2011-03-29
I used this guide to setup so Windows & Ubuntu could share my docs etc, simple but effective is how it works for me:

[http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/](http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/)

---

### Post by irv on 2011-03-29
> **Megaptera said:**
> I used this guide to setup so Windows & Ubuntu could share my docs etc, simple but effective is how it works for me:

[http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/](http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/)

Very good Howto. Thanks for posting it.

---

### Post by Megaptera on 2011-03-29
> **irv said:**
> Very good Howto. Thanks for posting it.

You're welcome!

---

### Post by ihatetryingtopickaloginna on 2011-03-29
Here's what I got on the laptop:

1 MB unallocated partition
/dev/sda1 ntfs 14.65G in size with 911.25MB unused
/dev/sda2 ntfs  100MB in size with  66.41MB and this is the boot
/dev/sda3 ntfs 283.34M size 

sda1 is labeled PQSERVICE
sda2 is labeled SYSTEM RESERVED
sda3 is labeled ACER and has a triangle symbol with exclamation point

---

### Post by irv on 2011-03-29
> **ihatetryingtopickaloginna said:**
> Here's what I got on the laptop:

1 MB unallocated partition
/dev/sda1 ntfs 14.65G in size with 911.25MB unused
/dev/sda2 ntfs  100MB in size with  66.41MB and this is the boot
/dev/sda3 ntfs 283.34M size 

sda1 is labeled PQSERVICE
sda2 is labeled SYSTEM RESERVED
sda3 is labeled ACER and has a triangle symbol with exclamation point

In your first post you said you have a 320 gig Hard Drive and if I did the math right I come up with about 17 gig total here and that is used and un-used. There's something wrong with this picture.

---

### Post by ihatetryingtopickaloginna on 2011-03-30
Yes I did say that. It's in the specs for the laptop and those numbers are what were on the screen of gparted. I would post a screenshot of it, but don't know how to paste it in here. On the top of the gparted screen it says /dev/sda3 283.34GiB so I'm assuming it is what is called a 320g drive.

If someone will tell me how to paste a screenshot in this message I'll do it.

Thanks

---

### Post by irv on 2011-03-30
> **ihatetryingtopickaloginna said:**
> Yes I did say that. It's in the specs for the laptop and those numbers are what were on the screen of gparted. I would post a screenshot of it, but don't know how to paste it in here. On the top of the gparted screen it says /dev/sda3 283.34GiB so I'm assuming it is what is called a 320g drive.

If someone will tell me how to paste a screenshot in this message I'll do it.

Thanks

There's two programs you could install to take screen shots. shutter and gnome-screenshot. Once you take the screenshot just use the paper clip when posting on this forum to paste in your post.
[ATTACH]187570[/ATTACH]   [ATTACH]187571[/ATTACH]
You can install it either from the package manager or the software center.

---

### Post by ihatetryingtopickaloginna on 2011-03-30
ok i just used my phone camera

---

### Post by ihatetryingtopickaloginna on 2011-03-30
uh oh a mistake, that is 283.34G not M

---

### Post by irv on 2011-03-30
> **ihatetryingtopickaloginna said:**
> uh oh a mistake, that is 283.34G not M

That's what throw me off.
If you were to just install Ubuntu it would take a slice of the 283.34Gig and use it for Ubuntu. If you are going to use this and do it your self you would have to shrink this partition using gparted but be careful and backup your data. After shrinking this partition you would have to setup your /home, /swap and your / partitions manually. If you have never done this before I would get some help locally. Do you have a user group in your area?

---

### Post by oldfred on 2011-03-30
I really prefer to partition in advance as then I have total control over how it is done & what sizes they are. Also make sure you have good backups. Some buttons on the auto install screens are confusing & both use entire disk. If you the manual install then there are no issues.

Issues on dual boot in same drive:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
From kansasnoob:
[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)
Trust me here! If you choose either "Use entire partition" or "Use entire disc" you are not likely to end up with "Alongside" anything! You will most likely lose the OS and any data contained therein!

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

Shared NTFS partition - You can also use links
[http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/](http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)

---

### Post by Jerry N on 2011-03-30
> **irv said:**
> That's what throw me off.
If you were to just install Ubuntu it would take a slice of the 283.34Gig and use it for Ubuntu. If you are going to use this and do it your self you would have to shrink this partition using gparted but be careful and backup your data. 

No No!  Don't shrink a Windows 7 partition with gparted.  Use the Windows 7 disk management tools.  Doing it with gparted _might_ work and then again it might farkle up the whole partition.

Jerry

---

### Post by ihatetryingtopickaloginna on 2011-03-30
> **irv said:**
>  If you have never done this before I would get some help locally. Do you have a user group in your area?

I have years ago in OS/2, but have forgotten most of it. Only did it a couple times if I remember correct. But it was just using the whole disk and formatting the partition for it. I have done it in Linux but again used the whole disk. Made a few messes once on a desktop trying to learn how to make different partitions. No user group that I know of.

---

### Post by irv on 2011-03-31
> **Jerry N said:**
> No No!  Don't shrink a Windows 7 partition with gparted.  Use the Windows 7 disk management tools.  Doing it with gparted _might_ work and then again it might farkle up the whole partition.

Jerry

I must be getting old. I was sure I shrunk my Windows 7 partition with gparted, but I went back and found the post I did it on, and I never touch it. If you want to see what I did just go to this thread:
[http://ubuntuforums.org/showthread.php?t=1595534 ]("http://ubuntuforums.org/showthread.php?t=1595534")
I did this in Oct 2010.
Sorry for giving the wrong advice here. I did shrink windows a few years ago but I did it in windows. I had to do a scandisk first to make sure there were no bad sectors on the drive.

---

