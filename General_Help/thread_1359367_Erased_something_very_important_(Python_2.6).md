---
title: "Erased something very important (Python 2.6)"
date: 2009-12-19
forum: General Help
---

### Post by linux_dream on 2009-12-19
I've uninstalled Python 2.6 from the Ubuntu Software center because I wanted to install the 3.0 version.  However, after the un-installation, a black screen appeared asking me to log in.  I can't enter my desktop anymore.  I don't know how I can reinstall Python 2.6 so that all becomes normal.
I'm sure this is somewhat a common problem.  
Please help me!  Thank you very much.

---

### Post by Darael on 2009-12-19
First off, try pressing ctrl+alt+f7 - it may be that your GUI is still there. If that doesn't work, log in and try running the following to reinstall python (it defaults to 2.6):
```
sudo aptitude install python
```

---

### Post by Cheesemill on 2009-12-19
The problem is that most of the default applications that come with Ubuntu need python to run. By uninstalling python you have also removed all these hundreds of apps.

Doing the following in a terminal:
sudo apt-get install ubuntu-desktop

Will get most of them back, but any of the non-default apps that you may have installed will need re-installing as well. It's going to be a long job to fix this.

PS - When you told Ubuntu to remove python it will have told you it was going to do this before you agreed.
PPS - You can have python 3 and python 2 installed at the same time without them conflicting.

---

### Post by linux_dream on 2009-12-19
> **Darael said:**
> First off, try pressing ctrl+alt+f7 - it may be that your GUI is still there. If that doesn't work, log in and try running the following to reinstall python (it defaults to 2.6):
```
sudo aptitude install python
```

I reboot and it said Ubuntu was running on a low graphics mode.  I tried the ctrl+Alt+f7.  The screen turned totally black.  After 2 minutes I restarted because nothing happened.
I then tried the sudo command but I got an error message and in order to get rid of the error I had to type another command of which I don't remember.  (it ended by -- a-).
I then tried to install Python, and it said it would "free" 266 Mb of space.  I said ok and it seems I uninstalled a lot of things instead of installing Python!  I reboot, and the problem is still here.  I retried to install Python and it said it would "free" 0 Mb.  I said ok and I'm still at the same point.

> **Cheesemill said:**
> The problem is that most of the default applications that come with Ubuntu need python to run. By uninstalling python you have also removed all these hundreds of apps.

Doing the following in a terminal:
sudo apt-get install ubuntu-desktop

Will get most of them back, but any of the non-default apps that you may have installed will need re-installing as well. It's going to be a long job to fix this.

PS - When you told Ubuntu to remove python it will have told you it was going to do this before you agreed.
PPS - You can have python 3 and python 2 installed at the same time without them conflicting.
Ok thanks I will try.
And no, it didn't say ANYTHING when I uninstalled Python 2.6.  It just asked my password if I remember well.  (or absolutely nothing).

I'm quite new to Ubuntu (2 weeks approximately) and I don't have a lot of things installed others than the actualizations and some programs provided by the Ubuntu Software center.

---

### Post by RJ12 on 2009-12-19
> **linux_dream said:**
> I reboot and it said Ubuntu was running on a low graphics mode.  I tried the ctrl+Alt+f7.  The screen turned totally black.  After 2 minutes I restarted because nothing happened.
I then tried the sudo command but I got an error message and in order to get rid of the error I had to type another command of which I don't remember.  (it ended by -- a-).
I then tried to install Python, and it said it would "free" 266 Mb of space.  I said ok and it seems I uninstalled a lot of things instead of installing Python!  I reboot, and the problem is still here.  I retried to install Python and it said it would "free" 0 Mb.  I said ok and I'm still at the same point.


Ok thanks I will try.
And no, it didn't say ANYTHING when I uninstalled Python 2.6.  It just asked my password if I remember well.  (or absolutely nothing).

I'm quite new to Ubuntu (2 weeks approximately) and I don't have a lot of things installed others than the actualizations and some programs provided by the Ubuntu Software center.

I think you have to be in Synaptic for it to tell you that info so next time you install something like Python please check the Synaptic Package Manager in System>Administration>Synaptic Package Manager to check any applications dependencies (What it needs and what other apps need it) or you can use the terminal and type sudo apt-get install packagenamehere


P.S. Welcome to Ubuntu I hope you enjoy it as much as me:)

---

### Post by linux_dream on 2009-12-19
I think I had downloaded Synaptic...
Anyway, I thank you all for all your help.  I'm replying from Ubuntu.  I've succeed in reinstalling the desktop.  I realize some of my programs are missing (as of now I found out that google chrome and amsn are not here anymore) but others are here.  
About Ubuntu... it's incredible.  I prefer it much more than my Windows XP (I'm dual booting) which is much, much, much slower for all.

---

