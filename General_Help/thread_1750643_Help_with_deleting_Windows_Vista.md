---
title: "Help with deleting Windows Vista"
date: 2011-05-05
forum: General Help
---

### Post by jayharper08 on 2011-05-05
So I've been running Ubuntu now for about a month and a half. I'm running low on memory and decided that I would rather go with Linux/Ubuntu instead of the Windows I have. Every time I try to run Windows, after about 15-30 minutes it freezes up and I can't do anything but pull the battery. On Ubuntu, no problems what so ever. So, all I do is browse forums pretty much and download music, nothing that I would absolutely NEED Windows for. I have it set with the dual boot set up now. I've looked and can't find any answers on how I would do this. I have seen the partitioning part of the forums and all, but no clear answer. So please don't flame me. I want to know if, and how I could keep my Ubuntu setup and just delete windows completely off my hard drive. I have already backed up my pics and important files so it can be wiped out. Is this even possible or what I just have to start back over? Thank you in advance :D

Oh, and I am running a Toshiba Satellite A305-s6905 with 3gb memory and 320 gb hd.

---

### Post by JugglinPhil on 2011-05-05
The easiest and probably quickest way is probably to simply back up all your stuff and reinstall Ubuntu, telling it to delete Windows.
Otherwise you have to find out what partitions Windows is using, boot from a Ubuntu Live CD, run the program "Gparted" and delete those partitions. Then you can extend your Ubuntu partition to fill the newly free space. 
However I am not sure how this will effect the Boot-Manager, and as always you should keep a back up of everything.
I'd go for the reinstall.

---

### Post by flipper T on 2011-05-05
if you have backed up all your important files, doing a full install of your chosen linux distro is the way to go.

full instructions here :


[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

---

### Post by jayharper08 on 2011-05-05
Alright. Thank you guys for the quick reply. I will go with a fresh install :D Really appreciate it. (and not flaming me)

---

### Post by kpuz on 2011-05-05
Alternatively, You could boot into the Ubuntu LiveCD and use gparted to format your Windows partition and then expand your Ubuntu partition to take over that space. May save you the hassle of reinstalling ubuntu. Make sure to back up what you need though as messing around with partitions can have unseen consequences.

---

### Post by jayharper08 on 2011-05-05
Alright thank you. Think im just going to start over with ubuntu. Im scared of doing that partition stuff lol.

---

### Post by colin.p on 2011-05-05
I just did that last week. I removed win 7, using GParted, creating a 155GB ext4 partition. I just use it as a storage partition, along with "/" and my "home". However, I left the "recovery" partition though, just in case I sell this thing.

---

### Post by wojox on 2011-05-05
> **jayharper08 said:**
> Im scared of doing that partition stuff lol.

Since your plan is to fresh install it wouldn't hurt to practice using gparted from a live-cd. That way if you mess it up you can still do your fresh install.

---

### Post by jayharper08 on 2011-05-05
> **wojox said:**
> Since your plan is to fresh install it wouldn't hurt to practice using gparted from a live-cd. That way if you mess it up you can still do your fresh install.

Yea I played around with it for a bit. Just got it up and running with only ubuntu. I installed the 11.04 version and its a little tricker then the 10.xx I had, lol. Getting used to it though.

This is the version I wanted to download before I did all this to get used to it, but I didn't have enough memory.

---

