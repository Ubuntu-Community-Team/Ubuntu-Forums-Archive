---
title: "ubuntu, virtualbox and win 7"
date: 2010-10-11
forum: General Help
---

### Post by karq on 2010-10-11
Hey everyone.

I'm thinking of making ubuntu my main os and deleting my win 7 dualboot and installing it on virtualbox. Does win 7 run smoothly on virtualbox?

I have a C2D 1,8Ghz, 2GB of ram laptop.

---

### Post by Quackers on 2010-10-11
I am thinking of doing the same thing. I installed VirtualBox a few days ago and then istalled Vista in there. It worked fine for 2 days and then I had problems getting it to start up. To cut a long story short I uninstalled everything and started again.
I installed VirtualBox-ose through Synaptic Package Manager and then put Windows 7 in there. So far it is running very well (much better than Vista did). But, in fairness, it's only been about 6 hours :-)  so although initial signs are good, I will leave it a few weeks before I take the plunge.

---

### Post by emoguitarist06 on 2010-10-11
Windows 7 works great
but I recommend not using the OSE version
but the propriety full version 
here [http://www.virtualbox.org/wiki/Linux_Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads")

---

### Post by techunit on 2010-10-11
A word of warning. Serious hardware is in need for such an endeavor. I would recommend at least a quad core proc, and 3 gigs of ram.

---

### Post by techunit on 2010-10-11
> **karq said:**
> Hey everyone.

I'm thinking of making ubuntu my main os and deleting my win 7 dualboot and installing it on virtualbox. Does win 7 run smoothly on virtualbox?

I have a C2D 1,8Ghz, 2GB of ram laptop.
I just looked at your specs and no. performance will probably be to slow to be beneficial... In your case I would recommend wine.

---

### Post by emoguitarist06 on 2010-10-11
> **techunit said:**
> A word of warning. Serious hardware is in need for such an endeavor. I would recommend at least a quad core proc, and 3 gigs of ram.

I am using a Asus Eee PC 1201N. Which has an Intel Atom 1.6ghc dual core and 4GB (only 3.25gb usable) of ram and I do not have any frustrations with running VirtualBox with Windows XP or 7 as the guest OS and I still have full function compiz (sphere/cube) and firefox running ;)

---

### Post by emoguitarist06 on 2010-10-11
OH if he only has 1 core then I would agree with you
but you can't virtualize in wine he can just hopefully run whatever windwos apps he's using in wine

---

### Post by pricetech on 2010-10-11
I'm running VMs with XP and Windows 7 both.  No problems with either.

I used the OSE version in the past.  This time I'm using PUEL version.  Can't tell a lot of difference.

---

### Post by lobralleo on 2010-10-11
I tested Win7 RC a while ago on a Intel Core2 Duo @ 2 GHz with 2GB RAM and an NVidia GeForce 8400GS, with Ubuntu 9.04 as host system. Win7 installs and runs smoothly, however the Aero interface does not work due to lack of graphic support (I believe it was a DirectX issue) within VirtualBox.

I was able to install and run software at an acceptable speed for basic usage - OpenOffice, Firefox, Gimp and the like, however did not try any game or graphic-intensive software.

As emoguitarist06 suggested, I would definitely go for the full version of VirtualBox for better support.

---

### Post by Quackers on 2010-10-11
> **lobralleo said:**
> I tested Win7 RC a while ago on a Intel Core2 Duo @ 2 GHz with 2GB RAM and an NVidia GeForce 8400GS, with Ubuntu 9.04 as host system. Win7 installs and runs smoothly, however the Aero interface does not work due to lack of graphic support (I believe it was a DirectX issue) within VirtualBox.

I was able to install and run software at an acceptable speed for basic usage - OpenOffice, Firefox, Gimp and the like, however did not try any game or graphic-intensive software.

As emoguitarist06 suggested, I would definitely go for the full version of VirtualBox for better support.

Those specs aren't much different from mine and although the graphics won't support gaming and there is a small amount of lagginess at times (which may yet be solvable) it is very usable.

---

### Post by lobralleo on 2010-10-11
> **Quackers said:**
> Those specs aren't much different from mine and although the graphics won't support gaming and there is a small amount of lagginess at times (which may yet be solvable) it is very usable.

Just today, a new version of VirtualBox (3.2.10) was released: I haven't checked the changelog, but it's quite possible that it could address performance issues.

---

### Post by Quackers on 2010-10-11
Thanks for the info lobralleo.
I am running 3.2.8_OSE r64453 and looking in Help menu I expected to find an update option. No sir, too easy :-) How would I update to the new one? Uninstall/re-install?

---

### Post by lobralleo on 2010-10-11
You're welcome, Quackers!

Usually, I just download the new .deb package from the VirtualBox website and install it over the old version; I never had any glitches and the VMs are automatically updated to the new release.

I think I remember they also maintain an Ubuntu-compliant repository, however I am not sure if it's ready for Maverick Meerkat.

---

### Post by Quackers on 2010-10-11
Thanks, I'll investigate/experiment/mess it up :-)

---

### Post by Quackers on 2010-10-11
oops :( maybe I should uninstall OSE first?

---

### Post by sendblink23 on 2010-10-11
> **Quackers said:**
> oops :( maybe I should uninstall OSE first?

You do know in the thread we were talking... I told you I was using the lastest version of VBox... I never knew you were using the old *USC version, I were assuming you were going to virtualbox.org and downloading it from there (no wonder vista had an issue for you previously) :P

---

### Post by Quackers on 2010-10-11
Hello my friend :-)
Before today I was using the latest version from VB website, but that's the one that flagged the errors.
This one from Synaptic is at least still working :-)
But I've never been one to shy away from a challenge (even a reckless one).
I'll uninstall OSE and try again with the shiny new one from VB. I suspect I may be in touch again.
In my own thread next time.

---

