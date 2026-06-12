---
title: "recover data?"
date: 2011-01-16
forum: General Help
---

### Post by michiganitis on 2011-01-16
Hello,

Well, my laptop slid off my couch and crashed down onto hardwood floor. The hard drive is shot. I was using grub and had both ubuntu 10.10 and windows 7 on it. Can't load either OS.

What options do I have for trying to recover data off the ubuntu partition? I tried loading livecd...for some reason, it won't work. Does livecd require a working harddisk?

What else can I do?

Thanks!

---

### Post by James78 on 2011-01-16
No, the livecd doesn't require a working hard disk. When you say the drive is shot, do you also mean to imply that it cannot be mounted at all? If it can be mounted, there's still a chance of recovery, and if not, your odds just went down significantly, but there may still be a chance regardless depending on exactly what broke. Does the drive make any noise; clunking, loose pieces, .. stuff like that.

---

### Post by michiganitis on 2011-01-16
> **James78 said:**
> No, the livecd doesn't require a working hard disk. When you say the drive is shot, do you also mean to imply that it cannot be mounted at all? If it can be mounted, there's still a chance of recovery, and if not, your odds just went down significantly, but there may still be a chance regardless depending on exactly what broke. Does the drive make any noise; clunking, loose pieces, .. stuff like that.

i can't boot to either os, livecd won't load ubuntu. not sure how to mount drive. the drive makes noise...it sounds like it's trying to access the same sector over and over and over and...yeah.

---

### Post by James78 on 2011-01-16
It sounds like a broken actuator arm (the 'arm' that moves around and reads data off of the hard drive platters). There are sometimes ways to get the hard drive arm to work long enough to get whatever you want off of it, and sometimes (probably most times) you can't do even that. It all depends.

So, before you can do anything, you'll need to get the arm working long enough before you can access any data off of the drive.

There's many many many temporary 'fixes'. Setting the drive on a completely level surface, sticking it in the freezer, all of these are "valid" to some extent, as many of them might or might not work; you don't know until you try.

I'm afraid I can't really help you on this, as there's too many ways. But please, search Google for search terms such as "fix hard drive clicking", "hard drive arm click fix", and the like. Good luck. ;)

---

### Post by michiganitis on 2011-01-16
I don't think it's the arm. Maybe I described the sound wrong. It sounds exactly like my old hard drive did went it tried read a bad sector over and over and over. I can get to the grub command line...but I don't think the grub command line is useful, is it?

---

### Post by James78 on 2011-01-16
It's either a broken arm (referenced by a continuous clicking sound), or what you said. Assuming it's a bad sector, then some data on the hard drive platters was damaged (easily possible). I'd agree that it's not likely you would get it to ever boot successfully, but you may still be able to recover some data. All I can really suggest you do is, somehow, get into a livecd, try to mount it, and try to get the data off.

You said the livecd doesn't work. What happens when you try to use it?

---

### Post by michiganitis on 2011-01-16
> **James78 said:**
> It's either a broken arm (referenced by a continuous clicking sound), or what you said. Assuming it's a bad sector, then some data on the hard drive platters was damaged (easily possible). I'd agree that it's not likely you would get it to ever boot successfully, but you may still be able to recover some data. All I can really suggest you do is, somehow, get into a livecd, try to mount it, and try to get the data off.

You said the livecd doesn't work. What happens when you try to use it?

with ubuntu livecd, i click 'try ubuntu'...i get the ubuntu version of the hourglass...and the little hourglass thing just keeps going around and around...forever.

---

### Post by goldshirt9 on 2011-01-16
you could always put in a hdd caddy and run it as a slave via another pc

then it would show up ( if use able) as a external hdd

---

### Post by James78 on 2011-01-16
Can you try running the livecd in safe graphics mode?
[https://help.ubuntu.com/community/BootOptions#Changing the CD's Default Boot Options]("https://help.ubuntu.com/community/BootOptions#Changing the CD's Default Boot Options")
> **goldshirt9 said:**
> you could always put in a hdd caddy and run it as a slave via another pc

then it would show up ( if use able) as a external hdd
Great alternative option. :p

---

### Post by michiganitis on 2011-01-16
Ok! I was able to load SystemRescueCD. All I know is graphical Ubuntu. SystemRescueCD is just a command prompt/terminal window sort of OS. What do I do now? I don't know how to see what drives/partitions there are...or how to mount them.

Thank you guys so much!

---

### Post by michiganitis on 2011-01-16
Ok...did some messing around. I was able to mount my linux partition. But then when I type 'ls', i got input/output errors on home, opt, proc, sbi, etc and sys. but i do see other directories. where would my 'desktop' be located?

---

### Post by James78 on 2011-01-16
Unfortunately, /home/user/Desktop. I hope you can get at your data on /home/user; if not, there's probably not much you can do I'm afraid.

---

### Post by James78 on 2011-01-16
I found this post here, it may help you to see how much you can recover.
[http://ubuntuforums.org/showpost.php?p=10363836&postcount=8](http://ubuntuforums.org/showpost.php?p=10363836&postcount=8)

---

### Post by michiganitis on 2011-01-16
> **James78 said:**
> I found this post here, it may help you to see how much you can recover.
[http://ubuntuforums.org/showpost.php?p=10363836&postcount=8](http://ubuntuforums.org/showpost.php?p=10363836&postcount=8)

Thanks, I may try that. My drive is toast for future use though, certainly.

Everything else is SEEMINGLY working fine. What else could possibly be break in a lap top when you drop it from about 3 feet onto a hard wood floor? It landed pretty much square on it's bottom...not a corner or screen or ac plug or anything.

Thanks!

---

### Post by James78 on 2011-01-16
> **michiganitis said:**
> Thanks, I may try that. My drive is toast for future use though, certainly.

Everything else is SEEMINGLY working fine. **What else could possibly be break in a lap top when you drop it from about 3 feet onto a hard wood floor?** It landed pretty much square on it's bottom...not a corner or screen or ac plug or anything.

Thanks!
Usually the screen and hard drive. If your laptop actually starts and whatnot, you should be fine in that regard. The hard drive and the screen are the most sensitive parts. Usually little pieces of the laptop break when it gets dropped, but it's usually not a huge huge issue; can sometimes get really annoying though (i.e. your lid doesn't stay shut anymore because of a broken piece) ;)

---

### Post by Costas100 on 2011-01-16
Some years back I had a major crash on a dual boot machine ubuntu/vista. The crash was mainly due to vista. I was unable to access my files (I wasn't very much worried about the operating systems - Vista was to be abandoned and Ubuntu I could reinstall). 
To rescue my files I used a small rescue program. I am not quite sute which one it was (some years have passed). In a list of possibilities you can try the following, top one first:
1. System rescue CD  [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)
2. Ultimate boot CD  [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)
3. Rip Linux CD      [http://twit88.com/blog/2010/08/13/rip-linux-linux-rescue-cd/](http://twit88.com/blog/2010/08/13/rip-linux-linux-rescue-cd/)

Unfortunately I do not remember which one I used and how I did it, but I managed to recover over 90% of my files

Good luck to you

Costas

---

