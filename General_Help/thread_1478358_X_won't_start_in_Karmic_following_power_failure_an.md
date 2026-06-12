---
title: "X won't start in Karmic following power failure and upgrade"
date: 2010-05-09
forum: General Help
---

### Post by clanmackay on 2010-05-09
Hello,

Yesterday or the day before, the Update Manager downloaded a bunch of packages, and prompted me for a reboot.  I chose "Reboot Later".  The reboot suggests to me that there might(?) have been a kernel upgrade in there.

Sometime between last night and this morning, the power failed.  The laptop (a Dell Latitude D810) was running on battery power.  It *may* have gone into hibernation.  I would guess that it did, based on my not noticing the appearance of the normal BIOS flash screen.

Resuming, I got the Ubuntu login screen (I have it set to bring up an X login immediately.)  The login screen looks different from how it did before, so I'm guessing it was upgraded.  There is now a message in the upper right informing me that a power management feature failed to install.

Entering my login info appears to work.  The Ubuntu loading graphic appears, then I am put back at the login screen.  This happens repeatedly.  If I enter an invalid username and password, login fails, so some authentication is clearly succeeding.

I rebooted and faced the same problem.  Ditto on switching back to the previous kernel.  Recovery mode in both kernels gives the same result: dpkg reports no errors, and startx fails with a "couldn't compile keymap" error.

So, I don't even know how to start working this out.  Package upgrade, kernel upgrade, Dell hibernation problems, and power failures all seem to be on the table.  Help?  Thanks.

---

### Post by Zgeek on 2010-05-09
I'm having the same issue. After the kernel upgrade to 2.6.31-21 I restarted as prompted, but later put my laptop (old compaq nx9010) into hibernation.  I am now experiencing the same symptoms.

---

### Post by solwic on 2010-05-09
Start with a clean install.  Some here will disagree, but upgrades are notorious for failing.  

Once you do that, see if the problems persist.  

Good luck.  :)

EDIT:  Hibernation/Suspend is also notoriously buggy in Ubuntu.

---

### Post by clanmackay on 2010-05-09
So ... is there any consensus that a clean install will help?  Should I upgrade to Lucid as long as I'm doing that?  Is this expected to be (reasonably) non-destructive?  And -- is there a chance that hibernation -- which worked before -- will work after that?  :-)

---

### Post by Zgeek on 2010-05-10
It appears as though some  people are having a  similar problem in 10.04. I found this thread: 

[http://ubuntuforums.org/showthread.php?t=1473152&highlight=Desktop+won%27t+start](http://ubuntuforums.org/showthread.php?t=1473152&highlight=Desktop+won%27t+start)

I followed the solution proposed by Bitter_Mike at the bottom of the 1st page which comprises of uninstalling the gdm, then reinstalling it. 

These are the steps I used and it solved the problem for me.

boot into recovery mode with networking, then at root prompt:

       stop gdm

       apt-get purge gdm

       apt-get install gdm

       reboot now

This got me to a blank desktop with a single terminal.

       apt-get install gnome-session

I was not able to apt-get the package indicator-applet-session for some reason, so I rebooted and got it from the package manager. 

My desktop is now back to normal :)... hope this helps

---

### Post by Zorael on 2010-05-10
If you can get to a terminal with a net connection, try configuring packages, then updating and upgrading from repositories.
```
$ sudo dpkg --configure -a
$ sudo aptitude update
$ sudo aptitude full-upgrade
```
As a sidenote, aptitude has a **reinstall** parameter if you just want to reinstall a single package. (apt-get doesn't)

---

### Post by Padapwa on 2010-05-10
> **solwic said:**
> Start with a clean install.  Some here will disagree, but upgrades are notorious for failing.  

Once you do that, see if the problems persist.  

Good luck.  :)

EDIT:  Hibernation/Suspend is also notoriously buggy in Ubuntu.

He's not doing a full system upgrade to a new version, just an update.

It's unfortunate that either can cause these kinds of trouble but it's well known to do that in Ubuntu when upgrading from one version to another.

I'd suggest you look for a proper solution in your log files, because while "just reinstall" might seem like a quick fix, chances are that you'll be back at the same point you are now once you update your system again.

Personally i have been running debian testing and Arch rolling release for over 5 years (actually debian is older than that but i can't really remember when i installed it the first time, the original install have travelled into new computers during this time) and i have NEVER had a problem i couldn't figure out by looking at the logs.

First thing, check out your X log, it seems to me this is either a proprietary video driver problem or a problem with an update to Compiz (i'm going to go right ahead and assume you are using that POS for a WM). Second thing, check the apt logs, check what it updated, revert or update again if there are new packages.

---

