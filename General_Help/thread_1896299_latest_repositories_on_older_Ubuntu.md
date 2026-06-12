---
title: "latest repositories on older Ubuntu"
date: 2011-12-16
forum: General Help
---

### Post by monkeyKata on 2011-12-16
Hello forum.

A few days ago I decided to reinstall everything and try out a new distro and so for the past few days I've been playing around on several: opensuse with KDE, mint with gnome-shell and MATE, Kubuntu... I ended up with a fresh install of an old Ubuntu 10.10.  I wanted to go with the latest mint but wasn't sold on gnome-shell and MATE crashed on me, plus I couldn't get Emerald to work on it (something about the latest version of Compiz not being compatible with it).  

Now, a fresh install, 10.10 is running smooth and quickly.  My question is this:  is there any way to change my repositories over from 10.10 maverick to 11.10 oneiric to have the latest updates on my software?  Or will this cause problems and likely break things?  Even using ppa's, I seem to be limited to the 10.10 maverick repositories.  I'd like to update the mint menu(downloaded from webupd8 ppa), for example, and maybe the kernal.

Any ideas?

---

### Post by zero2xiii on 2011-12-16
Hay,

That might cause some issues, seeing as the software is tested for the specific release of ubuntu before it is added to the repro. So it might cause instability esp if you take into concediration all the dependancies, if you want to run the latest, then run either a LTS or a latest release build (even the LTS is not gaurenteed to have all the latest, but it does have a beter support cycle for sotfware)

Cherz

---

### Post by snowpine on 2011-12-16
You can upgrade your 10.10 to 11.10 following these instructions:

[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

Unfortunately many users have indeed reported problems with the upgrade, therefore I recommend you perform a backup just in case. You may find it is quicker and easier to simply do a fresh install of 11.10. :)

---

### Post by gandaran on 2011-12-16
> Now, a fresh install, 10.10 is running smooth and quickly. My question is this: is there any way to change my repositories over from 10.10 maverick to 11.10 oneiric to have the latest updates on my software?
No, you will break you system! besides the dependency issue 10.10 runs on gnome2 while 11.10 uses gnome3, you cant run gnome3 applications on 10.10.
the best way to get some new software for 10.10 is using third party repositories like the [PPA's ]("https://launchpad.net/ubuntu/+ppas") and [getdeb]("http://www.getdeb.net/updates/Ubuntu/10.10/").

---

### Post by monkeyKata on 2011-12-16
> **gandaran said:**
> No, you will break you system! besides the dependency issue 10.10 runs on gnome2 while 11.10 uses gnome3, you cant run gnome3 applications on 10.10.
the best way to get some new software for 10.10 is using third party repositories like the [PPA's ]("https://launchpad.net/ubuntu/+ppas") and [getdeb]("http://www.getdeb.net/updates/Ubuntu/10.10/").

oh yes that's right!  I had forgotten about getdeb.  Thanks for the tip!

And thanks everyone for the feedback.  I went so far back in versions because I like the classic gnome2.  It's actually running well I probably won't update much.

---

