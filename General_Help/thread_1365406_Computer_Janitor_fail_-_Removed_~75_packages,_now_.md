---
title: "Computer Janitor fail - Removed ~75 packages, now mplayer wont start"
date: 2009-12-27
forum: General Help
---

### Post by Talix on 2009-12-27
Hey guys, Im pretty new to Linux so do not hesitate to use low level language ^^

I finally finished the compilation and installation of Mplayer with the windows codec CoreAVC yesterday. I also managed to install the front end SMplayer, and everything worked at last :D

Then I crashed my system by overloading the little guy (eeepc 901) with too many tasks, this was not really the bad thing, but giving up waiting for it after ten minutes was. I shut down the computer by powering it off... Thus creating some startup error with the power manager not being installed correcty. This again is not my current problem, because this one solved itself by being able to boot after a nights sleep :)

To clean up after the crash-mess I did some apt-gets on upgrades and eventual missing packages, found nothing new. Then I ran COMPUTER-*******-JANITOR ><

That was my real mistake. Ignorant as I was, it told me that I was not using these 75 different packages. "hmm," I thought. "It would be nice to get the extra 400MB space on a harddrive this size (2GB)", so I removed the lot, and not mplayer crashes. I tried doing both a  new "make install" and "make" from the source lib, but now it complains about a specific package it cant find:> /usr/bin/ld: cannot find -lopencore-amrnb
Is there a way of rolling back the changes of computer janitor?


(btw, I can not be 100% sure that it is computer janitors mistake here, because I did not try to start mplayer right after the crash, so of course it is possible that some packages may have become unreadable - I do not *think* so though...)

---

### Post by diablo75 on 2009-12-27
As "fun" as it is to compile from source code, it's almost always unnecessary for most apps, mplayer included.  Open up System>Administration>Synaptic Package Manager and do a search for mplayer.  You should be able to find it and mark it for installation (or reinstallation if it says it's already installed).  There are also a lot of other packages you can easily find and install with Synaptic, such as ubuntu-restricted-extras which will install a lot of video/audio codecs for you.

---

### Post by Talix on 2009-12-27
> **diablo75 said:**
> As "fun" as it is to compile from source code, it's almost always unnecessary for most apps, mplayer included.  Open up System>Administration>Synaptic Package Manager and do a search for mplayer.  You should be able to find it and mark it for installation (or reinstallation if it says it's already installed).  There are also a lot of other packages you can easily find and install with Synaptic, such as ubuntu-restricted-extras which will install a lot of video/audio codecs for you.
Dude, I'm sorry, but that doesn't help ;)

I'm not THAT new to linux. The reason for me to compile the code myself was because I had to port the pay-to-use windows only codec CoreAVC for H.264 HD-video playback.

I need to rollback the changes, I can't use SPM unless it has some kind of rollback... It does?

//EDIT:
The error message that displays when i try to run mplayer from the terminal (not smplayer - mplayer fails only when initiated from playback inn smplayer) is this:> mplayer: error while loading shared libraries: libopencore-amrnb.so.0: cannot open shared object file: No such file or directory

---

### Post by diablo75 on 2009-12-27
> **Talix said:**
> Dude, I'm sorry, but that doesn't help ;)

I'm not THAT new to linux. The reason for me to compile the code myself was because I had to port the pay-to-use windows only codec CoreAVC for H.264 HD-video playback.

I need to rollback the changes, I can't use SPM unless it has some kind of rollback... It does?

Wow, I'm stumped dude, ha ha ha.  Sorry.

---

### Post by Talix on 2009-12-27
> **diablo75 said:**
> Wow, I'm stumped dude, ha ha ha.  Sorry.
Haha, no problem friend ^^

Actually, I just solved the problem... Stupid as i am, I didn't think about just reinstalling whatever package mplayer was requesting. I only had to find 4 different ones (though SPM). The first one was "libopencore-amrnb", the second "libopencore-amrwb" and then two others.

Now it starts and I can go back to MAH SHOWS ;D

Freakin' Janitor removed btw -_-

---

