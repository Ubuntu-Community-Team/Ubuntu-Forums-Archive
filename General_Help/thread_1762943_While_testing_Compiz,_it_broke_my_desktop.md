---
title: "While testing Compiz, it broke my desktop"
date: 2011-05-19
forum: General Help
---

### Post by erind on 2011-05-19
Hi all,
Today, after some testing with compiz in my PC, I ended up uninstalling it again, because the video card didn't have the right specs.  So when I rebooted, my desktop started acting weird - the applications' top panels disappeared, they couldn't be moved around, no more usable workspaces, etc ... also the mouse pointer keeps on rotating indefinitely, making my OS practically unusable.
So is there any hope I can restore my desktop to its previous state, or do I have to do a full reinstall, which I'd like to avoid if possible ?

Using Ubuntu 9.10 Karmic, 64 bit, Gnome.
Thanks

---

### Post by 3Miro on 2011-05-19
9.10 is no longer supported. It is highly recommended that you install a newer version (like 10.04 supported until 2013 or 11.04 supported until 2012).

You can try to boot Ubuntu in fail-safe mode to see what is happening.

Other than that, my guess is that since compiz is considered part of your desktop, removing it may have removed something important (did you take a good look at the packages that you were removing). Unfortunately with 9.10 you can no longer use Synaptic or the Software Center to install things.

---

### Post by erind on 2011-05-19
> **3Miro said:**
> 9.10 is no longer supported. It is highly recommended that you install a newer version (like 10.04 supported until 2013 or 11.04 supported until 2012).

You can try to boot Ubuntu in fail-safe mode to see what is happening.

**Other than that, my guess is that since compiz is considered part of your desktop, removing it may have removed something important (did you take a good look at the packages that you were removing). **Unfortunately with 9.10 you can no longer use Synaptic or the Software Center to install things.

Thanks *3Miro*, your guess was right. When I removed compiz, I did a *complete removal, *which broke my desktop. Reinstalled it ( compiz-core ) and it's all good now.
Surely, sooner or later I'll be upgrading to a newer version.

---

### Post by 3Miro on 2011-05-19
> **erind said:**
> Thanks *3Miro*, your guess was right. When I removed compiz, I did a *complete removal, *which broke my desktop. Reinstalled it ( compiz-core ) and it's all good now.
Surely, sooner or later I'll be upgrading to a newer version.

You got lucky then. You probably had the .deb cached on your HDD, there is no way to download the .deb for 9.10 anymore (maybe there is some obscure repo server left, but not an official one).

Try to move to 10.04 as soon as you can.

---

### Post by wildmanne39 on 2011-05-19
> **erind said:**
> Hi all,
Today, after some testing with compiz in my PC, I ended up uninstalling it again, because the video card didn't have the right specs.  So when I rebooted, my desktop started acting weird - the applications' top panels disappeared, they couldn't be moved around, no more usable workspaces, etc ... also the mouse pointer keeps on rotating indefinitely, making my OS practically unusable.
So is there any hope I can restore my desktop to its previous state, or do I have to do a full reinstall, which I'd like to avoid if possible ?

Using Ubuntu 9.10 Karmic, 64 bit, Gnome.
ThanksHi, that just happend to me I had to use a laptop the other day that I have not use in three years, and I could not upgrade it to the next version of ubuntu because the repos not there anymore.

---

### Post by erind on 2011-05-19
> **3Miro said:**
> You got lucky then. You probably had the .deb cached on your HDD, there is no way to download the .deb for 9.10 anymore (maybe there is some obscure repo server left, but not an official one).

Try to move to 10.04 as soon as you can.

I'll definitely upgrade. Not sure what source I got the package from, I just went the same old way: *sudo apt-get install compiz-core*  and it did the magic.
Thanks again.

---

### Post by zia.newversion on 2011-05-19
> **wildmanne39 said:**
> Hi, that just happend to me I had to use a laptop the other day that I have not use in three years, and I could not upgrade it to the next version of ubuntu because the repos not there anymore.
Upgrading from repositories won't work. You'll have to download the image from Ubuntu website and write it on a disk or USB and then install... All additional details on [Ubuntu Homepage]("http://www.ubuntu.com").

---

