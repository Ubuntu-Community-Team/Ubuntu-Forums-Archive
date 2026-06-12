---
title: "I managed to ruin an Ubuntu upgrade from 8.04 to 9.04"
date: 2010-07-18
forum: General Help
---

### Post by Gannzter on 2010-07-18
Hi there guys, I was trying to make my Ubuntu 8.04 play 3gp files with audio and I learnt I had to install Realplayer. After downloading the .deb package, the package manager gave me an error message regarding the a certain libsound file. I then figure (wrongly in retrospect) that if I removed the package in the error message, realplayer would install.

No sooner had I began to remove the libsound (or so, I'm not quite sure) package, i knew there was trouble because I noticed it was removing packages related to other files including my google chrome installation. After removing it completely, google chrome stopped working and I could not even access my home/files via the GUI. I figured wrongly again, that maybe by upgrading to 9.04 the problems will be fixed.

The upgrade completed okay, I even say Jaunty's new desktop and then it required a restart (I was asked if it should remove some files during clean up and I told it to proceed). After the restart however, the 9.04 normal start up shows the splash screen and then takes me back to a full screen terminal, where it asks me for my username and password.

I have tried the "startx" command but it just shows a black blank screen with a mouse cursor. I have tried the recovery console but I end up back at the terminal.

I need help as I was really beginning to enjoy my adventures with Ubuntu/Linux.

My laptops specs are as follows:

HP Compaq nx6310
Intel Centrino Processor T1300 @ 1.66Ghz
1.512 Gb Ram
Intel onboard graphics processor
Dual installation of Windows XP pro on a separate partition and the Ubuntu 8.04 installation.

I know this whole thing seems like an idiots chronicle but I am new to Linux and I was just trying out stuff. I would really appreciate your feedback.

Thanks in anticipation

---

### Post by su-37 on 2010-07-18
First of all have you backed up? if so from my experience the easiest course of action would be a clean install. If you havent backed up, boot from the live cd and plug in a flash drive or ext hard drive, then copy your files/ whatever to it and then do the clean install.

And dont worry we were all new to Ubuntu at one time or another. 
Best of luck im sure someone will be able to help without the need for a clean install, just my two cents.:D

---

### Post by chriswyatt on 2010-07-18
I don't think I can help you much.  But have you tried checking the logs?  Might be some clues as to what's failing in there.

```
cd /var/log
ls -l | more
```

Then 'cat' followed by the file you want to look at.

Also if you accidentally uninstall stuff does it prevent it installing itself again on a reinstall?  I wonder if sudo apt-get install ubuntu-desktop might help at all?  That's what I would try anyway.

Another thing, it might be good looking through the old aptitude logs, I wonder if one of them is datestamped with the day that you (possibly) accidentally removed something important?  You never know.

---

