---
title: "Strange iPod Issue"
date: 2009-07-23
forum: General Help
---

### Post by lobf on 2009-07-23
Hey guys. I'm extremely new to Ubuntu, and I like it, but I'm having some issues with my iPod that I need to resolve to continue using it. 

First of all- 
I'm using Ubuntu 9.04
I have an AMD processor
My iPod is an 80Gb 5th gen video model

I was playing some music from my iPod when the sound started to get choppy. Coming from Windows, my first instinct is restart, to I go to the menu and shut down. 

After I reboot, I see that none of my music is listed in my iPod in Rhythmbox anymore. After some research, I conclude that because of the differences in the way Linux and Windows write to drives, the file that lists how to access my music was corrupted or deleted, because all of the music files were still in the itunes/control folder. So I decide to back up my music to my hard drive, delete it from the iPod, and use Rhythmbox to re-upload it.  

I've deleted it, and I've re-uploaded about 20% of my music again when the computer freezes completely, I can't get it to catch up for several minutes, so I shut it down again. Now Ubuntu recognizes a "USB Drive" with an iPod logo, but not "My iPod," and other Windows computers still see it no problem. 

Google and your IRC channel were no help, so I'm hoping one of you can give me a hand with this. How can I get Ubuntu to see my iPod again? 

P.S.

My ultimate goal is to get my music back on my iPod. Getting Ubuntu to recognize it seems like it should be the easiest method. I was considering putting a Windows partition at the end of the drive and pulling my music files off of the Ubuntu partition from there, but I was told I'd have problems installing a Windows partition if Ubuntu is the first OS on this drive, not to mention partitioned to ext3. Confirm? Deny? Details?

---

### Post by tacantara on 2009-07-23
I haven't worked with Rhythmbox, but I know that Banshee is one of the better programs to use when syncing iPods.  I used to have a Classic that I synced with Banshee, and it worked quite well.  If you have a copy of Windows, you could install it in a virtual machine (i.e. VirtualBox).  That's my current setup, and that allows me to run iTunes in virtual mode (which I need to do in order to sync my iPod touch, which doesn't work at all with Ubuntu).

> **lobf said:**
> 
My ultimate goal is to get my music back on my iPod. Getting Ubuntu to recognize it seems like it should be the easiest method. I was considering putting a Windows partition at the end of the drive and pulling my music files off of the Ubuntu partition from there, but I was told I'd have problems installing a Windows partition if Ubuntu is the first OS on this drive, not to mention partitioned to ext3. Confirm? Deny? Details?

I've heard the same with regard to installing a Windows partition when Ubuntu is your first OS.   I can't help you much with that.

---

### Post by lobf on 2009-07-23
> **tacantara said:**
>   If you have a copy of Windows, you could install it in a virtual machine (i.e. VirtualBox).  That's my current setup, and that allows me to run iTunes in virtual mode (which I need to do in order to sync my iPod touch, which doesn't work at all with Ubuntu).


Can this virtual machine access files on my Ubuntu desktop? 


> I've heard the same with regard to installing a Windows partition when Ubuntu is your first OS.   I can't help you much with that.


Bummer.

---

### Post by tacantara on 2009-07-23
**@ lobf**

With VirtualBox, you can set up a virtual "shared" folder that will allow you to grab files from Ubuntu.  If you decide to go the VB route, download it from their website (the one in the repos is very limited in capabilities), and be sure to download version 3.0 (people who have downloaded 3.0.2 have reported major problems with it).  Once you have VB installed, install the Guest Additions package - this will give you access to USB and a bunch of other important things.  The VB website is located at the link below:

[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by lobf on 2009-07-23
So the one I get from going to "Add/Remove Programs" is not the one I should have?

---

### Post by philcamlin on 2009-07-23
> **lobf said:**
> So the one I get from going to "Add/Remove Programs" is not the one I should have?

yes that is the one that has limited capabilities

the one from the repos is a OSE but the one from the site is not :popcorn:

---

### Post by lobf on 2009-07-23
Alrighty, I'm downloading the good one now. I'll bump this if I have any issues. Thanks guys!

---

### Post by DarinB on 2009-07-23
I would open a windows machine go to itunes and reformat the ipod, then remount it in ubuntu, that should fix all the problems. i had that problem in the beginning as well once i reformatted the ipod i was good to go. also you may want to try banshee, it is very versatile, i use rhythmbox but that is just what i am used to. even though it does not handle video and have to use floola to add video. floola seems to be able to add anything on your ipod. but not as music player just as an ipod music manager.

---

