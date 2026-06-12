---
title: "Toshiba NB200, natty and latency"
date: 2011-05-20
forum: General Help
---

### Post by GuiGuy on 2011-05-20
Having "upgraded" my Toshiba NB200 net-book to from 10.10 to 11.04, I now find there a major latency issues once the OS has been running for a few minutes. Menus take  several seconds to display and the visual feedback when typing text makes the net-book unusable.

Before I go back to 10.10, are there any "tweaks" worth trying?

TIA

---

### Post by wildmanne39 on 2011-05-20
> **GuiGuy said:**
> Having "upgraded" my Toshiba NB200 net-book to from 10.10 to 11.04, I now find there a major latency issues once the OS has been running for a few minutes. Menus take  several seconds to display and the visual feedback when typing text makes the net-book unusable.

Before I go back to 10.10, are there any "tweaks" worth trying?

TIA
Hi, make sure have activated the restricted drivers for your video card, and you might install top process so you can see clearly what is slowing your system down.

---

### Post by GuiGuy on 2011-05-20
> **wildmanne39 said:**
> Hi, make sure have activated the restricted drivers for your video card, and you might install top process so you can see clearly what is slowing your system down.

Yea, I've done both of those. The restricted drivers are affected by the "The driver is installed but not in use bug", as it does my three other PC running natty. 

Re top, there's nothing of significance I can see. 

Cheers

---

### Post by wildmanne39 on 2011-05-20
> **GuiGuy said:**
> Yea, I've done both of those. The restricted drivers are affected by the "The driver is installed but not in use bug", as it does my three other PC running natty. 

Re top, there's nothing of significance I can see. 

Cheers
Hi, I know natty uses a little more resources, but it should not be a problem with a newer computer.

---

### Post by linuxinstalledfromhdd on 2011-05-20
On newer "state-of-the-art systems it's always prudent to test them with a live usb stick before upgrading.. and taking the plunge..  I wish they would tell users this before upgrading with:

sudo apt-get update && sudo apt-get dist-upgrade


goodluck with that.

---

### Post by wildmanne39 on 2011-05-20
> **GuiGuy said:**
> Yea, I've done both of those. The restricted drivers are affected by the "The driver is installed but not in use bug", as it does my three other PC running natty. 

Re top, there's nothing of significance I can see. 

Cheers

Hi, you can also log in as ubuntu classic or ubuntu classic no effects they both should use less resources and your system will run faster.

---

### Post by GuiGuy on 2011-05-20
I've restored the netbook to 10.10, which in turn has restored the performance.

By the way, the resource hog under 11.04 was something called "seed" :confused: 

I think [Natty]("http://www.thefreedictionary.com/natty") in this case is a [misnomer]("http://dictionary.reference.com/browse/misnomer").

---

### Post by GuiGuy on 2011-05-20
> **linuxinstalledfromhdd said:**
>  I wish they would tell users this before upgrading with:
sudo apt-get update && sudo apt-get dist-upgrade

[RANT]
I have long since learned that linux, and ubuntu in particular, underlying philosophy is to keep it's users frustrated and and entertained, especially when it comes to "upgrades". I've been using Ubuntu since 2006 at least, and cannot recall a single update on any computer that when smoothly. It is bloody annoying. 

Now I am contemplating restoring my other boxes to 10.10 because of the stupid "driver is installed but not in use" thing. No desktop effects on any of the PCs that have been [s]downgraded[/s] upgraded.
[/RANT]

For these reasons I have become compulsive about backups. A restore is simple, although time consuming. As was the [s]downgrade[/s] upgrade dalliance. 

Cheers

---

### Post by GuiGuy on 2011-05-20
> **wildmanne39 said:**
> Hi, you can also log in as ubuntu classic or ubuntu classic no effects they both should use less resources and your system will run faster.

I am (was) already doing that! None of my "upgraded" PCs, mostly nvidia based, have desktop effects working any more. My reading of the matter is that this is a bug that was noted in the beta yet never fixed!!??

Maybe it's time to move on to another distro?

---

### Post by wildmanne39 on 2011-05-21
> **GuiGuy said:**
> I am (was) already doing that! None of my "upgraded" PCs, mostly nvidia based, have desktop effects working any more. My reading of the matter is that this is a bug that was noted in the beta yet never fixed!!??

Maybe it's time to move on to another distro?
Hi, I am using a nvidia card with unity and I have all effects including the cube working, there are instructions that have to be followed closely to get it to work in unity. Also the bug that says the driver is not being used, that is the bug!! it actual is being used if you activated it. 
Unity uses compiz, in compiz settings there is a plug in that says unity plug in,but you do not want to deactivate it, I did, and I had to reset unity.

---

### Post by linuxinstalledfromhdd on 2011-05-21
I'm on 10.10 right now. I'm loving 10.10 like a fat kid love chocolate. I'm going to do Natty for a while, and I may even wait until the next release of Ubuntu to try again.  Unity was not very appealing to me.  And my printer drivers made my printer spew blank pages until I was forced to reach around the back of the unit and unplug it in 11.04.  LOL

---

