---
title: "Monitor auto sleeps/standby/hibernates"
date: 2009-11-12
forum: General Help
---

### Post by Kevin_E on 2009-11-12
Been using Linux for more than a year now and this has been my first public announcement of me needing help.  :D  I'm trying to keep a cool demeanor, though, when actually I'm irritated beyond belief with this ongoing issue.

Ever since installing Hardy, I've been plagued with what you may call "monitor power issues".  Hardy, Intrepid, Jaunty--- these have (what I am assuming is) hibernated my monitor.  The reason why I assume this is because my usual blue indicator power light will turn orange when the screen goes black, and no backlight is seen.  Karmic--- now I am assuming it sleeps OR goes into some type of screensaver mode without showing a screensaver.  The power indicator will still be blue and the black screen will have the backlight halo.

Currently:
Assumption of screensaver mode made me realize that I never reset my screensaver prefs after upgrading (resetting, meaning that I did not deactivate it like I have been since Hardy).  So, I unchecked the "activate ss when comp idle" box.  Nope, still did it after a varying amount of time.  So, I chose different animated savers (since the default was black), but NO SCREENSAVER SHOWN when the screen went black.  I even set it for one minute (non-activated) and it still turned black after 5-10 min.

Assumption of some type of sleep mode filled my head.  I done the whole "never" slide bar thing for such actions but it failed.  I even REMOVED the gnome power management, but I still have the problem.  I've also checked BIOS for the heck of it and nothing wrong there.

I have searched high and low for scripts/codes (I have to search history for links if you need them) and used most (not all) that I believed would benefit me and my problem.  I'm at wit's end.

Specs:
```
(cat /proc/version)
Linux version 2.6.31-14-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009

(uname -a)
Linux meatroot 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

(Sysinfo)
Ubuntu 9.10 (karmic)
GNOME 2.28.1
Kernel 2.6.31-14-generic
4.4.1 (i486-linux-gnu)
Xorg version is unknown
.........the stuff that will probably hurt........
Nvidia graphic card
GeForce 7950 GT
PCI-E 16x
512 MB
550 MHz
NVIDIA UNIX x86 Kernel Module  185.18.36  Fri Aug 14 17:18:04 PDT 2009

```I've read too much on issues with Nvidia and Linux compatibility, and think that maybe I have no hope for a cure for this cancer.

If any more details are needed, bug me.

Thanks in advance for your quick replies.  I hope I get this solved before I watch another movie on here WITHOUT it going black. :popcorn:

---

### Post by Kevin_E on 2009-11-14
Ok.  Starting this evening, not only did it go into "whatever" mode, but it is now doing a standby, hibernate... something... where my blue power light becomes orange and the backlight is completely off.

---

### Post by ddarsow on 2009-11-14
install caffeine

---

### Post by Kevin_E on 2009-11-19
> **ddarsow said:**
> install caffeine

Well, I gave it a few days to make sure it continues to do what it's supposed to, and it's great.  :D

Appreciated the recommendation.

**edit**
I should mention to those with the same issue about the install.  At first, I didn't find it in the Synaptic Package Manager.  So, I searched for it and found the [Pragmattica]("http://pragmattica.wordpress.com/2009/10/21/caffeine-1-0-released/") website, which has install notes.  It's rather quick and simple.

```
sudo bash -c "echo 'deb [http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu](http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu) jaunty main' >> /etc/apt/sources.list"
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 569113AE
sudo apt-get update && sudo apt-get install caffeine
```

---

### Post by scouser73 on 2009-11-19
Thank you thank you thank you.  This is exactly what I have been looking for.  I was sick to the back teeth of the screens going to standby when I was watching films.

Let me return the favour by showing you their PPA on Launchpad: [[COLOR="Red"]**PPA | Caffeine**[/COLOR]]("https://launchpad.net/~caffeine-developers/+archive/ppa")

---

