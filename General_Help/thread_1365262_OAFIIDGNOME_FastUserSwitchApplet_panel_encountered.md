---
title: "OAFIID:GNOME_FastUserSwitchApplet panel encountered a problem"
date: 2009-12-27
forum: General Help
---

### Post by hwttdz on 2009-12-27
I'm getting a "The panel encountered a problem while loading "OAFIID:GNOME_FastUserSwitchApplet"." when logging in.  There are numerous threads with this, but I can't find one marked solved or with a working solution.  The two solutions I have not tried are installing the fast-user-switch-applet (because that package has been retired, apparently replaced by gdm which is installed) and installing ubuntu-desktop (because this is a flash drive installation and I don't have the space).  

It would be fantastic if people might give a little more advice.

---

### Post by dcstar on 2009-12-27
> **hwttdz said:**
> I'm getting a "The panel encountered a problem while loading "OAFIID:GNOME_FastUserSwitchApplet"." when logging in.  There are numerous threads with this, but I can't find one marked solved or with a working solution.  The two solutions I have not tried are installing the fast-user-switch-applet (because that package has been retired, apparently replaced by gdm which is installed) and installing ubuntu-desktop (because this is a flash drive installation and I don't have the space).  

It would be fantastic if people might give a little more advice.

This no longer applies to 9.10 installations, if you upgraded from 9.04 you should remove it from your system.

---

### Post by hwttdz on 2009-12-27
That's funny, because I installed straight from a 9.10 cd, so there must be a karmic package that references the old version.  Anyways, installing indicator-applet-session and adding that to the panel and removing the old one settled it.

---

### Post by Circa Lucid on 2010-02-04
THANK YOU! I've had this problem ever since I switched over to Karmic 32 Desktop. The Fast Switcher would work perfect from a fresh install  but would be broken after I update. I have 2 servers running Karmic 64 Server with ubuntu-desktop and it works perfect there but it would always break (I reinstalled the OS 3 times) on my desktop.

---

### Post by Godzemo on 2010-04-05
I had a similar problem when trying to get rid of an unrelated applet, and this solution worked a charm.

To anyone reading this- deleting your configuration files (as suggested in numerous other threads) **is not necessary** :)

---

### Post by leleobhz on 2010-04-17
This issue happens when i upgraded my 9.10 to 10.04 some weeks ago (To be more precise, ive used some packages from Lucid in karmic via apt-pinning). Since first gnome package got upgraded i have this error. Reading now, i saw the [indicator-applet-session]("apt://indicator-applet-session") wasn't installed here. Will logout and see if this applies to --> 10.04 upgrades too.

---

### Post by leleobhz on 2010-04-17
YAY!!!! Solved for Lucid upgraded installations. The owner can plz add something to this in topic title?

---

### Post by cristofaro on 2010-06-20
Thank you, this solution fixed my problem.  I fresh installed 10.04 and it was working fine until I installed a few new programs.  For anyone reading this thread not completely sure how to follow the instructions previously discussed just open a terminal session and type:

sudo apt-get install indicator-applet-session

The indicator applet session program can then be added to the gnome panel by right clicking it and selecting -> Add to Panel

---

### Post by EEE901 on 2010-10-16
> **cristofaro said:**
> Thank you, this solution fixed my problem.  I fresh installed 10.04 and it was working fine until I installed a few new programs.  For anyone reading this thread not completely sure how to follow the instructions previously discussed just open a terminal session and type:

sudo apt-get install indicator-applet-session

The indicator applet session program can then be added to the gnome panel by right clicking it and selecting -> Add to Panel

Works like a charm on a 10.04 installation! Thanks.

---

### Post by ZoLatKam on 2011-09-23
Ty to all.

Quick easy fix to issue. :)

---

### Post by AnushaSameer on 2012-01-31
go to your home folder

press cntl + h

then your home folder will display hidden files

check whether any of the folders is locked

right click on the folder then click "properties". In that Click "permissions".

In owner, change folder access to "create and delete files."

And then click "Apply Permissions to Enclosed files"

If you cannot see any locked folders then select all folders and do the above

---

