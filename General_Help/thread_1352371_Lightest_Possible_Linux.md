---
title: "Lightest Possible Linux"
date: 2009-12-11
forum: General Help
---

### Post by LookUpSeeBlu on 2009-12-11
Hello,

I want to install a linux distro, perhaps Ubuntu, and make it as light and efficient as possible.  The ONLY use for this would be to launch VMWare Player and run images from there.  I want to set it up so all work is done in the VM images and thus, want to save as much resources as possible to make these run efficiently.  

I don't want to start a war here but any suggestions on the distro, X system, and other ways to make this as efficient and resource friendly as possible while still able to run VMWare?

Thanks.

Kevin

---

### Post by hwttdz on 2009-12-11
There's always the ubuntu minimal install with your lightweight window manager of choice, the light manager I have experience with and like is xfce.

Here's a good thread on setting it up
[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)

And here's where you can get ubuntu minimal
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

nice small download too.

---

### Post by joes7 on 2009-12-11
I recommend Xubuntu. It works just as fine as Ubuntu, but it saves PC resources (for it doesn't come with OO, you must install it yourself).

---

### Post by invenit on 2009-12-13
> **LookUpSeeBlu said:**
> I want to install a linux distro, perhaps Ubuntu, and make it as light and efficient as possible.

I'm experimenting with the suggestions for a karmic minimal install at [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal) 

Icewm works great on my box (Dell Dimension 3000, 3 GHz, 1 GB RAM). :popcorn:

edit: after booting, System Monitor reports 86.4 MB of memory used; with Firefox running, this increases to 127+ MB

---

### Post by Leppie on 2009-12-13
I used to have a Debian minimal with E17 which after boot used something like 40mb of ram. Unfortunately E17 is not stable, so this may not be the best option.
Did you look into crunchbang (ubuntu based) as well?

---

### Post by kappa962 on 2009-12-13
If the only thing you're going to do is run VMs, XFCE is probably going to be heavier than you really want. At the very least, you should do a minimal install of it, and not the standard  Xubuntu install. See Distrowatch's [article on minimal Xubuntu]("http://distrowatch.com/weekly.php?issue=20090504#feature"). You can see [my minimal E17 howto]("http://ubuntuforums.org/showthread.php?t=1280189") if you want to try E17, but even that may be heavier than you need. Maybe try LXDE or Fluxbox. Whichever way you go, definitely start from the minimal command line install on an Ubuntu alternate install CD, as shown in both articles I've linked to.

---

