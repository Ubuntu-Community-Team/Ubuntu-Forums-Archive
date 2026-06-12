---
title: "Dual boot problems"
date: 2009-11-24
forum: General Help
---

### Post by jibby_1 on 2009-11-24
Hi all,
   
  I just installed Ubuntu 9.10 on my new pc, and I want to boot vista onto it, seeing that the rest of the family wants to use windows I have no choice. So I have decided to do a dual boot the two OS’s but when I put the vista CD into the computer at start up it just goes straight into to Ubuntu and does not load the CD and I have set the boot priority to CD/DVD drive then hard disk, so then I tried to load the CD within Ubuntu and it comes up with some error can anyone help me

---

### Post by mechro on 2009-11-24
If you installed 9.10 from a LiveCD then I assume the computer had no trouble booting the CD which probably means you have a faulty Vista disc. Try it in another computer if possible and/or take it back to the retailer.

---

### Post by jibby_1 on 2009-11-24
> **mechro said:**
> If you installed 9.10 from a LiveCD then I assume the computer had no trouble booting the CD which probably means you have a faulty Vista disc. Try it in another computer if possible and/or take it back to the retailer.

well when i do load the DVD within ubuntu i can see the files are on the DVD but when i try to open them it just will not do it.

---

### Post by mechro on 2009-11-24
Er... I've just had a horrible flashback to my XP days... I did once have a faulty XP installation which even borked the CD boot. I had to wipe the hard drive before the CD would boot again.

So, was Vista originally installed on the computer? Do you still have a Windows partition?

---

### Post by jibby_1 on 2009-11-24
> **mechro said:**
> Er... I've just had a horrible flashback to my XP days... I did once have a faulty XP installation which even borked the CD boot. I had to wipe the hard drive before the CD would boot again.

So, was Vista originally installed on the computer? Do you still have a Windows partition?

   [FONT=Verdana][SIZE=2]No I built the computer my self and installed Ubuntu cause a friend recommended it to me, so there has never been any windows OS and there has never been a partition on the hardrive.[/SIZE][/FONT]

---

### Post by mechro on 2009-11-24
> **jibby_1 said:**
> well when i do load the DVD within ubuntu i can see the files are on the DVD but when i try to open them it just will not do it.

I only have experience of XP but if you can't even open folders that  points to a faulty disc... just my opinion, I don't know for sure.

---

### Post by jibby_1 on 2009-11-24
> **mechro said:**
> I only have experience of XP but if you can't even open folders that  points to a faulty disc... just my opinion, I don't know for sure.

oh i can go into the floders but cant open the exe,

---

### Post by jibby_1 on 2009-11-24
It won’t have something to do with the filing system because I read that Ubuntu uses a different one to windows and that I have to create a separate NTFS partition to boot windows.

---

### Post by mechro on 2009-11-24
> **jibby_1 said:**
> oh i can go into the floders but cant open the exe,

Er... well no, you can't open an .exe. That's a Windows executable that needs a working Windows operating system to run. Can you open stuff like jpg's and txt files?

If the disc isn't faulty what are your BIOS settings for your boot devices? Can you still boot your Ubuntu LiveCD?

---

### Post by mechro on 2009-11-24
Perhaps some misunderstanding here. Basically, to install Vista you have to boot the Vista DVD. You can't "run" the DVD from Ubuntu.

---

### Post by jibby_1 on 2009-11-25
> **mechro said:**
> Perhaps some misunderstanding here. Basically, to install Vista you have to boot the Vista DVD. You can't "run" the DVD from Ubuntu.

    [FONT=Verdana]oh right I see, but when I read guides and other question people have asked that are similar to mine they seem to be of the general opinion that I need to format my hard disk then install vista first then Ubuntu on a separate partition or they will say use a partition manger within ubuntu and create a NTFS partition.[/FONT]

---

### Post by mechro on 2009-11-25
Well, yes there is a quite a lot of work involved. Your opening post implies you already know what you're doing but you couldn't get your Vista disc to boot.

If you already have Ubuntu installed it doesn't stop you installing Vista second, it's just a slightly different procedure.

Your first step is to make room for Vista by repartitioning/resizing/moving partitions that are on your drive. You can do that from Ubuntu (preferably the LiveCd) using a tool such as Gparted... **System > Administration > Partition Editor**... though that might now be Palimpsest in 9.10... I'm not sure... it's a similar tool anyway.

---

