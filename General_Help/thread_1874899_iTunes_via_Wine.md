---
title: "iTunes via Wine"
date: 2011-11-04
forum: General Help
---

### Post by crutch145 on 2011-11-04
I installed iTunes version 10.5 and am running via Wine.  When I open iTunes, it looks like it is opening just fine, but it only shows the outer part of the iTunes window (grey border), the Library column (left side of window)... but does not show the content in the bulk portion of the window.  It only shows a white blank space where I should be seeing music, iTunes Store, etc.  Any ideas?  I am running Ubuntu 11.10.  

Thanks,

Justin

---

### Post by doctorbighands on 2011-11-04
As far as I know, and as far as [this article]("http://www.psychocats.net/ubuntu/itunes") knows, you can't run iTunes in Ubuntu, no matter what you try.

The good news is that anything iTunes can do can be done in Ubuntu - playing music, watching videos, syncing an iPod/iPhone, buying downloaded music and movies, etc.

If you absolutely, positively must have iTunes, you could run Windows (or OSX, although Apple frowns on it) in VirtualBox. Of course, that means you need a copy of Windows, and it's not a true fix for getting iTunes to run, but it works. I used to think iTunes was the bee's knees, but I kinda think it sucks now that I've tried other apps and put some distance between me and it.

---

### Post by crutch145 on 2011-11-04
I'm setting up my sister-in-law with Ubuntu, and she has a new iPhone and iPad.  I know Banshee syncs music... but she also like to be able to sync photos as well.  Does Shotwell or any other photo library program allow for syncing of photos back/forth between iPhone/iPad and PC?

---

### Post by seabird74 on 2011-11-16
> **doctorbighands said:**
> As far as I know, and as far as [this article]("http://www.psychocats.net/ubuntu/itunes") knows, you can't run iTunes in Ubuntu, no matter what you try.Ok, I disagree. I have been trying to solve the same issues actually. I am running 32 bit system (because 64 bit won't work) and installed iTunes 10.0 just fine. I am now trying to work out 10.5 and have the same visual issue. Probably a Graphic bug that is fixable. 

Will let you guys know how this is going

---

### Post by eric-yorba on 2011-11-16
> **crutch145 said:**
> I'm setting up my sister-in-law with Ubuntu, and she has a new iPhone and iPad.  I know Banshee syncs music... but she also like to be able to sync photos as well.  Does Shotwell or any other photo library program allow for syncing of photos back/forth between iPhone/iPad and PC?
Shotwell can only download photos from an iOS device. I'm not aware of any non-proprietary software that lets you write photos back to the device.

---

### Post by Mark Phelps on 2011-11-16
> **seabird74 said:**
> Ok, I am now trying to work out 10.5 ...
Will let you guys know how this is going

Well ... best of luck to you.  If the WineHQ page about iTunes is any indication, the Bronze  rating for iTunes 10.5 indicates that SOME things will work, others will not.

See below:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347")

---

### Post by jmacx81 on 2011-11-20
I've seen places that the 64 bit isn't supported. I have 64 bit Ubuntu, I've tried to install the 32 bit itunes on is and it isn't working. Is this because I have a 64 bit ubuntu?

---

### Post by crow_bag on 2011-11-20
I've been experiencing problems trying to get Itunes 10.5 (32 bit) working aswell. It seems to install fine but when I try and run Itunes I get this message :

> Itunes was not installed correctly. Please reinstall Itunes.

Error 7 (Windows error 126)

I've been searching but can't seem to find an answer to this problem, I had tried to get Banshee to manage my iPhone 4 but although it can see my phone Banshee can't make any changes e.g. add music to the phone.

---

### Post by jmacx81 on 2011-11-23
I right click iTunesSetup.exe and click permissions and click allow executing under permissions. Then go back and right click and open with Wine Windows Program Loader. Then nothing at all happens. Any ideas?

---

