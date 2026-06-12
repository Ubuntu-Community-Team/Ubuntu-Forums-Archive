---
title: "MSI GX73x Ubuntu 11.04 won't RESTART."
date: 2011-05-01
forum: General Help
---

### Post by LittleJakub on 2011-05-01
Dear forumers,

since I've installed 11.04 I have been encountering a very work-disturbing fact.

When I start my laptop, from power off to on- everything goes fine, the login screen shows up, all works. If I turn it off, then start it up again- all is ok.

BUT! If from a turned on 11.04 I ask it to restart (reboot), the system goes power down, laptop powers up again, and as soon as the splash should be appearing- the herddrive led stops lighing up (which usually means that the system is loading) and two leds go up and start blinking endlessly (the Caps Lock icon and a led that looks like 2 arrows- one facing up and second facing down in a rectangle)- the only way out seems to be hard power off, and startup again- then all again works fine.

This situation never appeared on anly of my previous Ubuntu setups.

Hope You can help me- that really is annoying.

P.S. To clear out things I tried to do:

-install a pre-proposed kernel (didn't give positive results, switched back to 2.6.38-8)
-install x-org edgers PPA files (also nothing)
-tried the proprietary graphic driver (didn't help either)

Waiting for You guys, hope we can solve it together!

---

### Post by collisionystm on 2011-05-01
i had a similar issue where it froze furring restart. Had to manually shut if off. Caused some kind of compression error in the software. Made it to safe boot, restarted from there... worked fine ever since.

---

### Post by LittleJakub on 2011-05-01
Tried it, didn't help :(

But thanks for trying! Waiting for other solutuons ;)

---

### Post by ninjaaron on 2011-05-01
I'm experiencing a related but worse version of this problem that renders my computer unusable without a liveCD/USB.

[http://ubuntuforums.org/showthread.php?p=10752205]("http://ubuntuforums.org/showthread.php?p=10752205")

---

### Post by LittleJakub on 2011-05-01
A funny thing to add to the pile of problems. It HAS to be a single kernel option, and in default, cause if I install Kubuntu 11.04 it gives the same problem. Help!?

---

### Post by ninjaaron on 2011-05-01
That gives me an idea. There is a release candidate of the next kernel available for Natty, the 2.6.39-rc4

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-rc4-natty/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-rc4-natty/")

Here are the directions, should you choose to do this:
Download and then install the following IN THIS ORDER: first get the linux-headers file that ends with "all.deb". Second get the linux-headers file that ends with "i386.deb" or "amd64.deb" depending upon what architecture you need. Finally get the linux-image file that ends with "i386.deb" or "amd64.deb" again depending upon what architecture you need. Honestly it doesn't really matter what order you download them in, but you need to make absolutely sure that you install them in this order.

after that, just reboot.

I'm not really sure how I would go about doing this with from a liveUSB, but I bet it might work for you.

---

### Post by LittleJakub on 2011-05-01
the thing is that i've already tried that- with no effects ;(

---

### Post by LittleJakub on 2011-05-02
nobody knows..? :(

---

