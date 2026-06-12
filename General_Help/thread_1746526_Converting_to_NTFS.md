---
title: "Converting to NTFS"
date: 2011-05-01
forum: General Help
---

### Post by PsyclonJohn on 2011-05-01
Hello,

I'm not sure where to post this question, and I've been searching for an answer for this, but I haven't been getting any luck. Hopefully someone can help me out with this. 

So, I used to duel boot Windows Vista and Ubuntu. I used Ubuntu for everything, but used Windows Vista for Audio Production (it's a really big hobby of mine). I gave it a try on Ubuntu and everything runs real slowly with a gigantic 3 second lag. I simply can't have that. 

The problem is, the other day Windows suddenly stopped booting up and I was forced to uninstall it and make Ubuntu native. Well, I put my Vista disk in and it keeps telling me my hard drive isn't formatted to NTFS and I've looked around for tutorials on how to convert it, but when I do that it tells me it's NTFS already or C: drive doesn't exist. 

I don't know anything about drives on Ubuntu (or partitions), can anyone help me out with this? I typed in CONVERT x:/FS:NTFS which is supposed to convert it to NTFS. Now, I'm not sure what x: drive is because I've never seen it before until today. 

I've also tried Gparted and had no luck with that. It wouldn't let me make a new partition slot. 

I don't mind if I lose any data during this procedure (I've made a backup on a friends computer), I'll just duel boot again. 

Thank you!

---

### Post by techunit on 2011-05-01
How many partitions do you have on the hard drive? You should just install Windows to the old windows partition. You many need to remove that first. Also you will end up needing to reinstall GRUB afterwards.

---

### Post by PsyclonJohn on 2011-05-01
I'm unsure, I believe 3. When I go to Gparted I have 3 listings: /dev/sda1,/dev/sda2/,/dev/sda5

It says the file system is ext4,extended, and linux-swap. Gparted wont let me edit anything. I've tried to unmount it, as some tutorials said to do before creating new partitions, but it didn't work.

---

### Post by oldfred on 2011-05-01
Your X: drive is probably the CD itself.

Windows will install to a NTFS partition that is primary and has the boot flag.

You have to use gparted from a liveCD. LiveCDs usually mount the swap partition and you have to use swap off to unmount it.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Win7 forum
[http://www.sevenforums.com/](http://www.sevenforums.com/)

---

### Post by PsyclonJohn on 2011-05-02
I've read a good amount of the article until it started mentioning RAID. Since sda2 is extended, it's not really considered a partition. So, now I really have 2 partitions? 

> Your X: drive is probably the CD itself.

Now that I think of it, it probably is the CD.

> Windows will install to a NTFS partition that is primary and has the boot flag.

The sda1 partition is both primary (I think) and has the boot flag. I was unable to change/format it to NTFS, but I am able to format any of the other partitions (Only 2GB on sda5, and that's not enough for Vista).

> You have to use gparted from a liveCD. LiveCDs usually mount the swap partition and you have to use swap off to unmount it.

This one, I'm a bit confused with. I don't have any options when I right click sda1, but I have options to change the swapon and swapoff in sda5. I logged on to ROOT a little while ago to see if there was any differences in modification, and there wasn't.

What I want to do though is split sda1 in half (if possible) and allow Ubuntu to use 100 GB and Vista 100 GB.

---

### Post by oldfred on 2011-05-02
Are you using a liveCD? You cannot use gparted from your Ubuntu install.

If you split sda1 in half and make a new partition it will be sda3 or 4 which still is primary. Then you can format that & set boot flag.

Resizing an Ubuntu System Partition Use liveCD so everything is unmounted & swapoff if neccesary
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

---

### Post by PsyclonJohn on 2011-05-02
I'm using 11.04, but have a 10.04 disk in front of me, would that work?

---

### Post by PsyclonJohn on 2011-05-02
Okay so, I put in my Ubuntu 10.04 LiveCD, I was ABLE to edit and change the file system to NTFS, but when I loaded up the Windows CD it said it wasn't NTFS. It also said there wasn't any free disk space, no idea why because I'm only using 5% of the space up.

---

### Post by oldfred on 2011-05-02
It does not see Linux partitions. If you have unallocated space you have to have a free primary partition. And if you have created a primary NTFS partition it has to have the boot flag (active partition in windows).

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by PsyclonJohn on 2011-05-03
At first I didn't know what you meant when you said "unallocated space", but now that I remember clearly, when I used Gparted from the LiveCD there was a listing called unallocated. It only shows up when the disk is inside my PC. I'll give it a try again.

---

