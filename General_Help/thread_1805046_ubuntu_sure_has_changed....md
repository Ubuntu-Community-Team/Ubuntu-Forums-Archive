---
title: "ubuntu sure has changed..."
date: 2011-07-15
forum: General Help
---

### Post by renodude18 on 2011-07-15
Alright, this isnt my first round with ubuntu and certainly wont be the last lol. anyway i recently installed ubuntu 11.04 via WUBI (Make way for the wubi sucks comments lol), so far i've had no problem with it everything works but i cant access the files on the drive that ubuntu is installed under. Here is how it is setup on this machine. I have the original 80GB hard drive with windows vista installed working fine, yes i used the words vista and working at the same time! my other drive is a 250 gb hard drive i use for my music and media storage on this machine. thats where i have ubuntu installed because obviously it has more space than the 80gb. but is there anyway i can get to my files on that drive. I am open to also installing ubuntu traditionally but dont think that i really should need to cause i had 9 on like this before.
Thanks for the help and this is all i think i need help with for now.

Dell dimension 8300 desktop full tower
Intel pentium 4 2.8GHZ HT
1.5GB DDR Ram
Windows vista biz SP2 on 80GB HDD
Ubuntu 11.04 on 250GB Wubi install drive
Nvidia Geforce 6200 512mb AGP
Soundmax? Onboard audio
Soundblaster Live 5.1 PCI Audio, works but would rather not use
DVD+/-RW Drive (HP) reads discs but wont play encrypted DVDs- yet!
-Works pretty good for a nearly 10 year old system!-

---

### Post by renodude18 on 2011-07-15
**Bump**

---

### Post by Hugh971 on 2011-07-15
Never used wubi so that might make things different but I'll try and help.

Ubuntu normally will be under a different partition. I think wubi uses virtual disks and I'm not quite sure how that works.

Linux uses Ext* file systems which windows can't deal with by default. You can read them using certain software such as Ext2read ([http://ext2read.blogspot.com/](http://ext2read.blogspot.com/)) though.

Apparently the virtual disks for Wubi are located in C:\ubuntu\disks\

---

### Post by WorMzy on 2011-07-15
Look in /host.

---

### Post by renodude18 on 2011-07-15
> **Hugh971 said:**
> Never used wubi so that might make things different but I'll try and help.

Ubuntu normally will be under a different partition. I think wubi uses virtual disks and I'm not quite sure how that works.

Linux uses Ext* file systems which windows can't deal with by default. You can read them using certain software such as Ext2read ([http://ext2read.blogspot.com/](http://ext2read.blogspot.com/)) though.

Apparently the virtual disks for Wubi are located in C:\ubuntu\disks\

Thank you for the reply Hugh971! Wubi does kinda complicate things a bit but i'm sure there is a way. I dont really need to access the files from ubuntu in windows but thanks for the link, i'll use that in case i do in the future. But i'm mainly trying to read the files that are on the same drive as ubuntu is installed. which does not have a OS, but it is formatted in NTFS for windows. again thanks for the response and help!

---

### Post by renodude18 on 2011-07-15
> **WorMzy said:**
> Look in /host.

I checked most all files in there thinking it would be there because in other versions of wubi/ubuntu i was able to see the files on the drive in the file system folder, they were then accessible but now idk where they all went. there still there as windows which i'm on right this second is able to access them still. Thanks for the help!

---

