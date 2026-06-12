---
title: "Is speed not a concern?"
date: 2011-01-28
forum: General Help
---

### Post by jsteel on 2011-01-28
Hi,

I've come to Ubuntu from Arch. I'm tired of fiddling with my system; I want something that's ready to go. I like Unity with the global menu and button integration, as my main computer is a netbook, so screen space is very precious.

I have a few concerns though.

1) There are a few processes that run in the background that eat away at my CPU/battery. These are beam.smp and update-apt-xapi. The beam.smp chews about 5% of my CPU consistently and the update-apt-xapi eats 100% from time to time for a few minutes. I dislike things happening in the background when I've not asked it to do anything.

2) The application indicators use far too much CPU imo. When I click on one and move my mouse over others (so they drop down in turn) my CPU goes up to about 40%; for a menu?! To compare, the normal GNOME menu uses about 7% when I hover around it.

I'm running Unity 2D (in 10.10) in the hope that this would be less intensive than the Compiz version but it doesn't seem to be any lighter.

I wonder if the 11.04 release will address my concerns, or if speed is not an issue for the Ubuntu devs; do they assume everyone has a fast/new computer?

Thanks

---

### Post by nothingspecial on 2011-01-28
Ubuntu has a different philosophy to Arch.

The idea is that the ordinary person at home installs it and everything is there and ready to go, "linux for human beings" they used to say. That includes stuff that you may or may not want. Bluetooth, broadcast accounts etc etc etc.

With arch you build from the base up.

If you would like to use ubuntu, I suggest doing a minimal install and building from there.

There are many pages on the web that show you how to have a ready to go system from a minimal install. Look at this for example

[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)

---

### Post by jsteel on 2011-01-28
Thanks I was not aware of this minimal CD. I will give it a go!

---

### Post by amsterdamharu on 2011-01-28
For (most) daemon processes upstart is used. Daemon processes might take up some CPU and memory.
I could see what upstart processes are running if you post the output of:
```
ls /etc/init/
```
It might be useful to not automatically start some daemons.
Please don't just delete or rename these files or you can't start them manually

I guess unity is cpu intensive, I've never used it. It is a starting project still although going to be released again with Ubuntu 11.

Not sure what the update-apt-xapi does.

---

