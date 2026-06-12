---
title: "WinXP/7 user going to Ubuntu, games, video editing, issues?"
date: 2010-03-21
forum: General Help
---

### Post by Pastortom on 2010-03-21
Hi..

I've used Windows XP most of my computer-life, and recently installed Windows 7 on my PC (Asus P5P77Deluxe, i5 CPU, 4gb dominator).. but to my surprise, its lagging =/ I only recently bought this computer, and the only thing I can think off being the "bottleneck" would be the 2x 9500gtx nvidia cards.. but still, shouldnt lagg with windows 7 and games with low set graphics? (Star Trek Online for instance)..

Anyways, 

I have some experience with Ubuntu, as I did a shuttle+4xscreen project a while back that lasted good for about 6 months, with 4x screens as a huge landscape.. I also recall the game "WOW" working wonderfully under Wine..  but since Ive FINALLY quit wow, and started playing STO (Star Trek Online), I wanna make sure this game actually works with Ubuntu, before starting using it again.. 

So my questions are:

1) Will Star Trek Online work fine with Ubuntu? If so, with Wine? Im talking full graphics, and no issues..

2) Will video editing work fine with Ubuntu? Like Pinaccle Express under Wine? or does there exist similar programs made for Ubuntu?

3) Can I run Ubuntu as 64-bit? What are my advantages there compared to 32-bit? My CPU is a Intel Quad-core i5 2,8ghz, so it sholdnt have any problems running whatever..

4) I also have 2 sata-cards installed (VIA and Sil), no issues with these using Ubuntu? (Ive got in total 12 harddrives hooked up, ranging from 75gig 10k rpms, to 2x2terrabytes .. all sata2.. 

Thanks on beforehand, for saving me the trouble of searching the forusm for 8 hours :) I kinda miss Ubuntu, loved using it back in the days, and especially loved Compiz with my 4xscreens :)

---

### Post by Revolutionary101 on 2010-03-21
1) I don't know. Sorry, but I have never tried Star Trek online.

2) I don't know if Pinaccle Express will work with Wine, although Ubuntu has several video editing applications. There is Kino, Pitivi, Kdenlive, Cinelerra. If you are looking for a professional video editing software, choose Cinelerra. Although if you are looking for an easy video software, pick Pitivi. Pitivi works and functions just like Windows Movie Maker. Also If you are looking for an application that can convert multiple video and audio codecs use Avidemux. Avidemux has support for several codecs and offers many advanced encoding features.

3)You can get Ubuntu in 64-bit but the only advantage is you will be able to use more than 4 GB of RAM. I guess you might not need it with Ubuntu because it is so light on system resources. However, I suggest that if you are able to use the 64-bit version of Ubuntu, it doesn't hurt to install it.

4)I don't know, sorry.

I hope that I have answered some of your questions about Ubuntu. I also hope that you will come to love it like I have.

---

### Post by bkcevilmonkey on 2010-03-21
1) WineHQ says it will run, but not flawlessly: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=19203](http://appdb.winehq.org/objectManager.php?sClass=version&iId=19203)

2) nothing about pinnacle on WineHQ, but theres lots of video editing programs that work, openshot is my favourite (it does greenscreening).  You could always try pinnacle in wine and see how it works for you.

3) I have the 64bit and I wish I didnt.  If you have more than 4gb of ram then for sure get the 64bit, but otherwise do 32bit.  Everytime I click on a .deb and see "improper architecture" I sigh heavily to myself.

4) The best way to try this is to boot from a live cd.  If they work from the livecd, then they'll surely work when you install it.

---

### Post by fluffman86 on 2010-03-21
1) Always check appdb.winehq.org for tips and tricks to get programs running properly in Wine.  Looks like STO should work, with a few tricks.

2) appdb says that pinnacle has a "garbage" rating, meaning it doesn't run at all.  I used to do some video editing in Sony Vegas 5 around 2003, and never could find a decent replacement when I first switched to Ubuntu in 2007.  I recently had to do some more minor editing and PiTiVi is actually really decent now, and will be installed by default in the next version of Ubuntu, so I suggest you give it a shot.

2.5) For other wine hacks, I suggest you install PlayOnLinux.  It makes a lot of the most common problems that users have with using wine go away by setting a new profile for each program.

3) 64-bit rocks.  It's way faster than 32bit, even with only 1GB RAM.  Everything in the Ubuntu repositories works flawlessly, and installing a .deb (like a .exe for Windows) requires a double-click if you find a 64bit version, or you just have to type "sudo dpkg -i --force-architecture program.deb" from the command line.  But you'll rarely have to do this, so don't worry. ;)

4) I use SATA in my computer, no problems here.  Linux treats as much hardware as posible as if it were generic so more of it works.  I've never had a problem with Hard Drives, thumbdrives, or ethernet ports in Linux, but constantly have to install drivers (even if it's automatic) for them in Windows.

---

### Post by bkcevilmonkey on 2010-03-21
> **fluffman86 said:**
>  type "sudo dpkg -i --force-architecture program.deb" from the command line. 

Man, I've never tried this...I wish someone told me about that years ago.

---

