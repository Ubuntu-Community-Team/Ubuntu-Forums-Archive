---
title: "Broken packages, instability"
date: 2010-06-22
forum: General Help
---

### Post by EMR on 2010-06-22
So, a friend's computer, running 8.04, refused to boot for a while, so I took a look at it.  It appeared to boot fine, but when I got to the login screen, it crashed when I started typing.  I did a hard power-off, booted it up again, and tried to update the packages (it has been disused for a few months, and I suspected that the problems had been fixed).  Synaptic told me that I would have to uninstall a bunch of packages in addition to updating, which was all fine and good, but then it crashed at the end of it's purge, and left me wondering if the system would be stable afterwards.  The update manager told me that I had broken packages, but then went on updating a few of them.  When I went back to synaptic, it disagreed, showing no broken packages.  I tried to open Firefox, but then GNOME crashed, so now I'm here.  

It has a pretty good internet connection, but how do I do a mass reinstall of all of the packages, and do I do this before or after I update the packages?

---

### Post by snowpine on 2010-06-22
Your post is a little short on specifics :) but I will try my best to help.

A good first step is to check for hardware problems: run memtest, check the filesystem for errors, maybe open the case and clean out the dust bunnies.

Next I would recommend going into System->Administration->Software Sources and uncheck any suspicious PPAs or 3rd-party repositories that you think might be causing stability problems.

Finally, this series of commands should get you back towards a working default Ubuntu desktop:

```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install ubuntu-desktop
```

---

