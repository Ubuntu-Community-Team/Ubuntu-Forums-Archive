---
title: "So do iPod Touches just not work on Ubuntu at all?"
date: 2011-04-24
forum: General Help
---

### Post by prettymess on 2011-04-24
I've been able to get Rhythmbox to at least acknowledge my iPod Touch, but when i try and add music to it, my iPod still says "No Content."  It looks like it syncs, when Rhythmbox is transfer the music to my iPod it even says that it's syncing on the iPod, but when I check to see if there's any music, there never is.

I've searched and haven't been able to find any solutions, but I've seen a lot of old threads with people that have this problem.  Has any been able to transfer music onto an iPod Touch successfully at all?

I'm using Ubuntu 10.10, by the way.

---

### Post by brpylko on 2011-04-24
Do IPods even connect to anything besides iTunes? Try installing iTunes in WINE.

---

### Post by prettymess on 2011-04-24
> **brpylko said:**
> Do IPods even connect to anything besides iTunes? Try installing iTunes in WINE.
I've successfully used an old iPod Video i had a while ago with Rhythmbox and it worked perfectly.

Haven't tried iTunes with Wine, but I can't imagine that working too well.  I might try it later.

---

### Post by drewsus on 2011-04-24
Dont bother with iTunes through WINE. Simply unlock your ipod touch after connecting it.

---

### Post by wolfen69 on 2011-04-24
As I mentioned in another thread, my ipod touch works great in ubuntu 11.04 with gtkpod.

---

### Post by oracle2b on 2011-04-24
Try this.

> sudo add-apt-repository ppa: pmcenery/ppa
sudo apt-get update
sudo apt-get install ifuse gtkpod mp3gain faad faac lame gtkpod-data id3v2 libid3-3.8.3c2a libmp4v2-0 vorbis-tools libimobiledevice1

---

### Post by Rasa1111 on 2011-04-25
I got my friends ipod touch working perfectly under Ubuntu 10.10. 
All I did was follow this simple instruction.. [http://www.webupd8.org/2010/12/get-ios4-mountsync-working-in-ubuntu.html](http://www.webupd8.org/2010/12/get-ios4-mountsync-working-in-ubuntu.html)

and it works perfectly! ;)

---

### Post by prettymess on 2011-04-25
> **Rasa1111 said:**
> I got my friends ipod touch working perfectly under Ubuntu 10.10. 
All I did was follow this simple instruction.. [http://www.webupd8.org/2010/12/get-ios4-mountsync-working-in-ubuntu.html](http://www.webupd8.org/2010/12/get-ios4-mountsync-working-in-ubuntu.html)

and it works perfectly! ;)
Yeah, I already did that.  That's how I was able to get my iPod to show up in Rhythmbox; however, when I add music to it, the files don't show up on the iPod.

> **wolfen69 said:**
> As I mentioned in another thread, my ipod touch works great in ubuntu 11.04 with gtkpod.
I just tried gtkpod, but adding music didn't work on that either; however, when I clicked "Check iPod's Files" it ended up showing all the songs I've been trying to add to it, but they were all listed in a playlist titled "[Orphaned]"  Any idea on what that means?  Or what I should do next?  I feel like I'm getting closer to getting this all figured out, so I really appreciate your guys' help!

---

### Post by prettymess on 2011-04-25
Anyone?

---

### Post by drewsus on 2011-04-25
Did you even read my comment? That is exactly what I had to do with every iPod touch I have connected to 5 different systems with 10.10.

---

### Post by prettymess on 2011-04-28
> **drewsus said:**
> Did you even read my comment? That is exactly what I had to do with every iPod touch I have connected to 5 different systems with 10.10.
Unless I misunderstood you, it didn't work.  Mind explaining it better?

---

### Post by drewsus on 2011-04-28
> **prettymess said:**
> Unless I misunderstood you, it didn't work.  Mind explaining it better?

Sure (and sorry if I came off rude, just wanted to make sure you didnt skip a potential solution). 
You likely did what I suggested correctly, but you connect the ipod, let Rhythmbox recognize it and then go to your ipod and swip+enter your keycode to unlock it like normal usage and it should now work. Or maybe unlock it before selecting to open it with Rhythmbox.   
Unfortunately I dont have one handy to try and help you further, but that is what I had to do in the past to get it to work. 
Good luck dude.

---

### Post by prettymess on 2011-04-29
> **drewsus said:**
> Sure (and sorry if I came off rude, just wanted to make sure you didnt skip a potential solution). 
You likely did what I suggested correctly, but you connect the ipod, let Rhythmbox recognize it and then go to your ipod and swip+enter your keycode to unlock it like normal usage and it should now work. Or maybe unlock it before selecting to open it with Rhythmbox.   
Unfortunately I dont have one handy to try and help you further, but that is what I had to do in the past to get it to work. 
Good luck dude.
Didn't work unfortunately. :(  Thanks for the suggestion, though!

Anyone else have any ideas?

---

### Post by morgue on 2011-04-29
This fixed some issues i was having with my iPhone not mounting, maybe it can help:
sudo apt-get install libimobiledevice-utils
idevice unpair
idevice pair
idevice validate

---

### Post by BookishBluestocking on 2011-04-29
> **morgue said:**
> This fixed some issues i was having with my iPhone not mounting, maybe it can help:
sudo apt-get install libimobiledevice-utils
idevice unpair
idevice pair
idevice validate
I'm having similar problems with getting my iPhone to mount. I tried what you suggested, but the terminal is giving me "idevice: command not found." Is there something missing from the command or something?

---

### Post by morgue on 2011-08-01
> **BookishBluestocking said:**
> I'm having similar problems with getting my iPhone to mount. I tried what you suggested, but the terminal is giving me "idevice: command not found." Is there something missing from the command or something?

my bad it's not idevice, it's idevicepair

idevicepair unpair
idevicepair pair
idevicepair validate

---

### Post by jusskan on 2011-08-15
> **morgue said:**
> This fixed some issues i was having with my iPhone not mounting, maybe it can help:
sudo apt-get install libimobiledevice-utils


That's what I get after inserting the suggested command: 

> E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?



advice?


thanks in advance, 

juss

---

### Post by Nubzilla on 2012-03-16
Hi
im probly on the wrong thread but any one know how to install ubuntu  to a ipod touch 3rd gen 32gb ipod touch what im thinking is ipod+running linux distro = small pc and no more itunes or stupid syncing ? is it possable

---

### Post by superbike on 2012-03-16
funny this my shows up as an attached device:guitar:

---

### Post by jwbrase on 2012-03-16
> **prettymess said:**
> I just tried gtkpod, but adding music didn't work on that either; however, when I clicked "Check iPod's Files" it ended up showing all the songs I've been trying to add to it, but they were all listed in a playlist titled "[Orphaned]"  Any idea on what that means?  Or what I should do next?  I feel like I'm getting closer to getting this all figured out, so I really appreciate your guys' help!

I'm not at all familiar with the iPod, but, as an educated guess from what you're seeing here, I'd say that it means:

1) The iPod's software needs files to be in playlists to be able to show them.

2) Rhythmbox and gtkpod are transferring files, but not putting them in a playlist on the iPod, either because they aren't capable of doing so, or because you don't know how to get them to do so.

3) gtkpod, however, knows that the files should be in a playlist (which probably indicates that it can put files in a playlist if you can figure out what you need to do to make it do that), and is showing them as being in a dummy playlist called "[Orphaned]" because they aren't in a playlist.

As to what you should do next: I'd say the odds are at least 10-to-1 that you don't need to install anything further or do anything further on the technical side. You probably just need to figure out how to use the features of Rhythmbox or gtkpod. You know how to get them to talk to the iPod, now you just need to know how to tell them what to say, so to speak. 

Unfortunately, I don't do a lot with music, and don't own an iPod, so I don't know an awful lot about Rhythmbox, gtkpod, or the iPod, so I can't really give you any specific instructions.

---

### Post by Elfy on 2012-03-16
OPs not been back since last year.

Closed.

---

