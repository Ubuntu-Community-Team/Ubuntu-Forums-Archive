---
title: "What's with iTunes and Ubuntu?"
date: 2010-12-13
forum: General Help
---

### Post by Wuxin on 2010-12-13
I was trying to listen to some of the Beatles samples that were recently released on iTunes.  For some reason Ubuntu rejects iTunes and I can't  listen to the Beatles!  What goes on here?  I'm not any great fan of iTunes but is there some reason it isn't compatible with Ubuntu?

---

### Post by slooksterpsv on 2010-12-13
Probably the way it handles the web site of the iTunes store I haven't tried bur I'd you have a copy of xp that you can install that and then install iTunes on that with virtual box il try later and see what happens

---

### Post by cascade9 on 2010-12-13
*bleugh* Well, it should run under WINE, if you get the right version- 

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347)

---

### Post by Rodney9 on 2010-12-13
Can I run iTunes in Ubuntu (or Linux in general)?
No, you can't. People will tell you there are weird ways to get iTunes running in Ubuntu, but I've never seen anyone successfully do it or give instructions that someone else could follow to successfully run iTunes in Ubuntu. If you do somehow manage to get some version of iTunes running, it will be buggy and not fully functional. There are two helper programs&#8212;Wine and Crossover Office&#8212;that allow you to run some native Windows programs, but even those don't work. If you don't believe me, check out these pages:

Wine application page for iTunes
Crossover Office application page for iTunes

If you must run iTunes, your best bet is a dual boot. This means you have to reboot your computer every time you want to access iTunes and then reboot your computer again if you want to use Ubuntu. Two slightly more convenient variations of this are running virtual Ubuntu inside Windows using Virtualbox (or running virtual Windows inside Ubuntu using Virtualbox) or having two computers and a KVM switch that allows you to quickly switch back and forth between Windows and Ubuntu using the same monitor and keyboard.

All of those are workarounds.

The bottom line is that you cannot run iTunes in Ubuntu. If you want iTunes, you need a virtual Windows environment or an actual Windows environment (or a Mac).

Your best bet is still to find a native Ubuntu alternative.

What's the best way to manage my iPod without iTunes?
There are actually many native Linux programs for managing your iPod. You can see on Wikipedia a comparison (including lists of features) of iPod managers.

AmaroK and Banshee in particular often come highly recommended from Ubuntu Forums members.

Up until recently there was no consistently reliable way to sync the iPhone with Linux. Ubuntu 10.04 and Ubuntu 10.10 include something called libimobiledevice, which helps users manager their iPhones and iPod Touches in Ubuntu with only some minor sacrifices in functionality.

What's the best way to get music without iTunes Music Store?
As of Ubuntu 10.04, if you go to Applications > Sound & Video > Rhythmbox Music Player, you will see that a music store is integrated into Ubuntu (and if you use the Ubuntu One online data storage in Ubuntu, music purchased through that store will be automatically backed up to "the Cloud").

Rhythmbox also has plugins to interact with Magnatune and Jamendo.

Here are some more details about alternatives:

    * Jamendo allows artists to publish their music under a free license for non-commercial use (if the artist wants to go commercial later, too, that's okay). So all downloads are completely free in every way (unless you're trying to scam money off the artist). A lot of French music, but also random other stuff. There's good French music, though. I'm kind of a pop music lover myself, so my favorites are Julandrew and Mel's.
    * Magnatune is a non-evil label that sifts through artists to find the best in... mainly trance and electronica (with smatterings of rock and folk). Half of the purchase price for songs goes directly to the artist. You can also listen to full albums (not 30-second clips) online for free.
    * The Amazon MP3 store has quite a wide selection and is your best electronic bet for mainstream popular commercial music.
    * eMusic sells a lot of songs from independent music labels (and even a few mainstream artists). Don't know that the artists get 50% of sales, though.
    * Uh... buy CDs. There's something nice about having CDs. You have a full backup of all your electronic music. It's higher quality (though I can't tell the difference between CD quality and 128 bitrate for MP3). Go to your local record store... or even shop online.

For more information, including user experiences and recommendations, read these Ubuntu Forums threads:
Best place to download music?
Where do you get your music?
Legal Music Downloads
music download for Linux

---

### Post by Wuxin on 2010-12-13
[FONT=Times New Roman][SIZE=4]Hmm.  This is very odd.  What does Apple have against Linux?  Or is it Linux against Apple?  I thought Linux was supposed to work easily with just about anything--that's it's great calling card!  Apple is also a UNIX based system so I would think there would be some degree of compatibility, no?  

I like Mac computers and think they offer a great package.  The reason I turned to Linux, however, is because I got sick of the proprietary boundaries of Mac.  Macs work just fine so long as you remain in the Mac world.  Once you venture out of it by trying to add new programs, etc., you often run into problems.  I'm guessing that the attempt to use iTunes on a Linux platform is another place where Apple draws the proprietary line.  It still seems strange...why would Apple turn down an opportunity to make more money?  
[/SIZE][/FONT]

---

### Post by diandal on 2010-12-13
Hi im no ubuntu expert, infact quite the opposite, fairly newbie from windows, but i have managed to install itunes 10 on my ubuntu 10.04 with wine 1.38

If you havent yet got wine, get it from ubuntu software centre and then download and save the itunes file and then open with wine.

---

### Post by ScottyD135 on 2010-12-13
I think that even if you could find some way to get itunes installed, it's going to be flaky at best.  Services are bound to not work properly (i.e. store, syncing, etc.).

I guess I think that while itunes is nice, I don't need it for basic music downloading.  Amazon.com has an MP3 downloader available FOR linux and seems to have a pretty thorough library of music for sampling and purchasing.

Also, with ipod support available in rhythmbox and other apps, my needs are more than met with these solutions.

My 2 cents...

---

