---
title: "Can't get out of power save mode"
date: 2009-12-25
forum: General Help
---

### Post by asano_man on 2009-12-25
I'm not sure if this has anything to do with Ubuntu, but it's annoying and I thought I'd start here for help.

First off, I'm running Karmic on an Inspiron 530, which is not exactly the best technology to begin with.  Also, since I'm a first time user of Ubuntu, I'm in a sort of frenzy trying to get things to work, looking at all the new things and all that, which only intensified when I found the software center.

I won't get into a whole lot of detail, just that I've downloaded a lot of things, messed a few things up here and there, but nothing seemed that serious.

And then when I walk away from the computer one day for a longer than usual time, I come to the hibernating screen that I can't get out of.  I have to force shutdown my computer to get out of it.  It's annoying because now I can't leave my computer alone for more than 15 minutes.

Feel free to call my all sorts of names if you feel the need to because I have no idea where to go with this.  If it's any help, below is the history of my recent downloads:

ubuntu-restricted-extras (36)
dvdisaster (0.72~rc1-1)
dvdisaster-doc (0.72~rc1-1)
wine1.2-dbg (1.1.35-0ubuntu1)
wine1.2-dev (1.1.35-0ubuntu1)
imagemagick (7:6.5.1.0-1.1ubuntu3)
libwxbase2.8-0 (2.8.10.1-0ubuntu1)
libwxgtk2.8-0 (2.8.10.1-0ubuntu1)
playonlinux (3.6-1)
python-wxgtk2.8 (2.8.10.1-0ubuntu1)
python-wxversion (2.8.10.1-0ubuntu1)
kamefu (0.1.1-4ubuntu1)
kamefu-data (0.1.1-4ubuntu1)
kdelibs-data (4:3.5.10.dfsg.1-2ubuntu7.2)
kdelibs4c2a (4:3.5.10.dfsg.1-2ubuntu7.2)
libavahi-qt3-1 (0.6.25-1ubuntu5.1)
libkamefu0 (0.1.1-4ubuntu1)
liblua50 (5.0.3-3build1)
liblualib50 (5.0.3-3build1)
libqt3-mt (3:3.3.8-b-5ubuntu3)
libqt3-mt-sqlite (3:3.3.8-b-5ubuntu3)
libsdl-net1.2 (1.2.7-2)
mednafen (0.8.C-0ubuntu1)

---

### Post by bapoumba on 2009-12-25
System > Prefs > Screensaver
Please try to set it up to a blank screen. If you have it set up to a screensaver using 3D acceleration, it may mess up with your video.

---

### Post by koba101 on 2009-12-25
check your power settings as well to see if anything's wrong there

---

### Post by asano_man on 2009-12-25
[[COLOR=#980101]**bapoumba**[/COLOR]]("http://ubuntuforums.org/member.php?u=171805"): yeah, that fixed that up.  I still don't know why it was doing it, though.  I'm absolutely sure it was something I did, because up until yesterday, I wasn't having a problem with it.  I haven't messed with the power settings, but I checked anyway and all seemed to be in order.  It might just be my crappy computer pulling it's same crap with me. :/

---

### Post by Mahngiel on 2009-12-25
there's a known issue from returning from suspend or other issues with karmic.  there's a bug report i don't have the sobriety to look for at this moment. it does however, have nothing to do with the programs you've installed. it's a kernel issue, and no swap space large enough nor any work around has been found.

best thing i can tell you, from being a notebook user myself, is to disable all hibernation / suspend capabilities.  i use the screensaver + screen lock for when i'm not going to be around. sure, the system is still active, but i don't have to hard boot.

---

### Post by asano_man on 2009-12-25
Ah, thank you.  I'm glad to know that this isn't just some stupid mistake on my part.  I think I can go without hibernation and suspend since I'm not usually away from the computer all that often.  It's not like it saves me much power anyway.

---

