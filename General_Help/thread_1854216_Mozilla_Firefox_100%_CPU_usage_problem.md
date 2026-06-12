---
title: "Mozilla Firefox 100% CPU usage problem"
date: 2011-10-03
forum: General Help
---

### Post by aoniumo on 2011-10-03
This would happen two-three times every 15 minutes.  Firefox would freeze and the computer screen would dim/darken and after about 15-30 seconds everything is ok again.  Is this a virus, bug, plugin incompatibility.

Here's a list of addons installed (firefoc v7.0.1)
Adblock Plus 1.3.10
Global menu bar integration 1.0.7
Noscript 2.1.4
Roomy bookmarks toolbar 1.3.0
Ubuntu firefox modification 0.9.2
WOT web of trust 20110704

Here's a screenshot from system monitor:

---

### Post by vasa1 on 2011-10-03
Go to add-ons and disable all add-ons and see if the problem persists after restarting.

If there's no problem, enable add-ons, one at a time and restart each time.

If you're lucky, it will be a single add-on that's the problem and not two conflicting add-ons.

I've had high CPU usage using AdBlock Plus because of a single filter. As soon as I modified that filter, CPU usage calmed down.

---

### Post by lovinglinux on 2011-10-04
Also try to optimize your Firefox databases. See [http://www.webgapps.org/tutorials/firefox/optimization/database-optimization](http://www.webgapps.org/tutorials/firefox/optimization/database-optimization)

---

### Post by mr_niceguy on 2011-11-21
I had the same issue and it turned out to be a conflict between the open source and binary video card drivers for NVidia.

For some reason if you install the proprietary binary driver from NVidia you now have to explicitly remove the nouveau (open source) driver before things work correctly.

```
sudo apt-get remove xserver-xorg-video-nouveau
```

---

### Post by cookiecruncher on 2012-02-11
> **mr_niceguy said:**
> ```
sudo apt-get remove xserver-xorg-video-nouveau
```

Didn't fix my problem.

---

