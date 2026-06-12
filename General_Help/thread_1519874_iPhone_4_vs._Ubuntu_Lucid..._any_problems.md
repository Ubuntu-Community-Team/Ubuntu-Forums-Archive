---
title: "iPhone 4 vs. Ubuntu Lucid... any problems?"
date: 2010-06-28
forum: General Help
---

### Post by couzin2000 on 2010-06-28
I'm an iPhone 3G owner, and I have had the pleasure of seeing my iPhone finally get functional with Ubuntu. With Lucid Lynx, connecting is now a sintch.

Obviously someone had the great idea of making another iPhone, thus making me spend more money. Question is: **anyone have any problems connecting to _Lucid_ with their new _iPhone 4_?**

I'd like to know about technical problems, if there are any, or good experiences in bringing music or (insert other functionality here) from Ubuntu into the iPhone. I'me very interested in buying one, so being a Ubuntu user I thought I'd ask here.


*PS: I **know** about the left-handed-signal-loss problem, so please keep those to yourself. I'm more interested in whether the phone connects to Ubuntu or not.*

---

### Post by aysiu on 2010-06-28
[libimobiledevice](http://www.libimobiledevice.org/) says: > 22.06.2010: iOS 4 is released and basic libimobiledevice functionality works fine. libgpod music syncing is broken right now but should work soon. What we know for sure is that iPad music syncing is not supported.

---

### Post by birdmanuk on 2010-06-30
My iPhone 3g didn't have any problems, connected to 10.04 and worked perfectly. My new iPhone 4 doesn't play so well. It doesn't even get picked up by ubuntu :-(

---

### Post by Mandor_ on 2010-07-01
USB tethering with ipheth is all broken, I'm assuming because either the driver or libmobiledevice don't recognize the iPhone 4 as of yet. I worked around it by installing iTunes inside a virtualbox and setting its network card to be a "shared connection" but it kinda sucks having to do that.

---

### Post by collectperth on 2010-07-08
all posts suggest we need to wait before upgrading iphone to os 4, stick with or go back to os 3, i have os 3 and am going to wait

---

### Post by kpanse on 2010-07-12
When I sync my music using RhythmBox does not work. Says transferred but I see nothing. But I guess its a known issue from above?  Just wanted to mention one more occurrence.  Also it duplicates Default playlists in the iphone once synced.

---

### Post by cyberey66 on 2010-07-12
My iPhone shows up in nautilus, but it does not show the music or let me transfer anything.

I built the latest libimobiledevice and no gain.  Someone on youtube commented on getting the iphone4 to work but I take that with a grain of salt.

---

### Post by TheForumTroll on 2010-07-12
> **cyberey66 said:**
> Someone on youtube commented on getting the iphone4 to work

So would I ;)

---

### Post by solotwit on 2010-07-15
I just plugged in my iphone4 and it was recognized. I'm using 10.04 and 64 bit. Rhythmbox thought it was an ipod and wanted to initialize, and fspot opened up to manage the photos. Not a bad start.

---

### Post by red_yanagi on 2010-07-28
> **solotwit said:**
> I just plugged in my iphone4 and it was recognized. I'm using 10.04 and 64 bit. Rhythmbox thought it was an ipod and wanted to initialize, and fspot opened up to manage the photos. Not a bad start.

I am running 10.04, too.
I can see my iphone4 on nautilus and fspot, and I can move my pictures on it.
but how can I send music files?
All I want is just listen music, rhythmbox does nothing currently.

---

### Post by Groundscrew on 2010-07-30
> **solotwit said:**
> I just plugged in my iphone4 and it was recognized. I'm using 10.04 and 64 bit. Rhythmbox thought it was an ipod and wanted to initialize, and fspot opened up to manage the photos. Not a bad start.

Same issue here i'm afraid.

---

### Post by red_yanagi on 2010-08-04
It seems to me that ios 4 needs special authentication for initialization.
I have initialized it by itunes, most recent version was needed of course.

Once you initiate it on itunes, you can see music library on rhythmbox too.

but, it is not easy to run itunes over virtualbox.
I used vmplayer instead.

hope this helps...

---

### Post by cyberey66 on 2010-08-06
> **red_yanagi said:**
> Once you initiate it on itunes, you can see music library on rhythmbox too.

but, it is not easy to run itunes over virtualbox.
I used vmplayer instead.

hope this helps...

Can you clarify what you mean by initiate?  I have iTunes running fine in virtualbox, but I cannot get rhythmbox to see my music library.

I have the latest version of libimobiledevice installed, which claims support for the iPhone 4 in rhythmbox.  

The jailbreak is now out, so one could possibly sync using SSH but that is a pain.

---

### Post by red_yanagi on 2010-08-11
> **cyberey66 said:**
> Can you clarify what you mean by initiate?  I have iTunes running fine in virtualbox, but I cannot get rhythmbox to see my music library.

I have the latest version of libimobiledevice installed, which claims support for the iPhone 4 in rhythmbox.  

The jailbreak is now out, so one could possibly sync using SSH but that is a pain.

I synchronized everything available in itunes. 

It was my first time to use itunes so I can't exactly remember.

I had to enter my itunes ID/password because it complained it doesn't know some applications I bought in iphone.

I had to sync with itunes for all apps in iphone to upgrade ios 4.0.1.
And I made some playlist and uploaded mp3s,

that's all I did in itunes.

Now rhythmbox shows my iphone's music library from the beginning if it is connected.
of course I didn't do the jailbreak.

---

### Post by truethug on 2010-08-12
I am running 10.04 64bit my phone shows up in nautilus rhythmbox and fspot.  Rythmbox says it is syncing my music am phone say's it's syncing, but it hangs.  I eventually unplugged my phone and the music I was adding was not there.

---

