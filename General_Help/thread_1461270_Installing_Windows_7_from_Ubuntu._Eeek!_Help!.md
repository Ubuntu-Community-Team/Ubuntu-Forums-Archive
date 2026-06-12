---
title: "Installing Windows 7 from Ubuntu. Eeek! Help!"
date: 2010-04-24
forum: General Help
---

### Post by Daners on 2010-04-24
Ok, so I am in my Ubuntu right now (it is my only OS). I have about 250gig of free space on my hard drive which I created as an NTFS partition (not sure if that was the right thing to do or not). But anyhow, I have my windows 7 cd, and I'm not sure how to go about installing it into that free 250gig partition. I've heard I should format everything and install windows first, then Ubuntu right after, but the only thing is, I have a HUGE music library saved in Ubuntu and I don't want to lose it, and I have no external hard drives or DVD cds to copy it to. Any help would be great, thanks people!

---

### Post by seenthelite on 2010-04-24
[This]("http://ubuntuforums.org/showthread.php?t=1035999") may help you.

---

### Post by wilee-nilee on 2010-04-24
> **Daners said:**
> Ok, so I am in my Ubuntu right now (it is my only OS). I have about 250gig of free space on my hard drive which I created as an NTFS partition (not sure if that was the right thing to do or not). But anyhow, I have my windows 7 cd, and I'm not sure how to go about installing it into that free 250gig partition. I've heard I should format everything and install windows first, then Ubuntu right after, but the only thing is, I have a HUGE music library saved in Ubuntu and I don't want to lose it, and I have no external hard drives or DVD cds to copy it to. Any help would be great, thanks people!

I would not do anything until you backup that stuff up off the computer. Personally I am not sure what happened but I had 2 W7 installs make my Lucid partition unallocated. I did do custom installs those times and let W7 build the partition; the correct size was used, rather then putting a NTFS there first with gparted, I suspect that was the problem but I am not sure.

---

### Post by Daners on 2010-04-24
Ok, so I made a windows partition and what not, and I boot up from the Windows 7 cd. Now when it boots from the cd it has the black screen like "Loading windows files" or something, then shows the little windows logo and says "Starting windows" then it goes to a blue wallpaper with the cursor and appears to be loading something (this is usually where a window pops up and you begin the installation) but nothing happens. No windows pop up, its just a blue wallpaper and I can move the cursor around, thats it. Any ideas on why this may be happening?

---

### Post by wilee-nilee on 2010-04-24
I hope you backed everything up first of all, beyond that where did you get the install disc from? I have 2 W7 pro DVD's, got sent a extra and a ISO download for loading a thumb or burning a DVD, and a install from a running MS install. Not a problem with any of them, but they are all MS products gotten from them.

Did you ruin the ms program to see if your computer is compatible, I assume MS provides a version that will check other then MS OS.

You might run from linux sudo fdisk -l so we can see the partitions. l=small case L

---

