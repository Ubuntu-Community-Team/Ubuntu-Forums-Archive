---
title: "Is there a power monitor for ubuntu 11.10?"
date: 2011-11-25
forum: General Help
---

### Post by molipha on 2011-11-25
Something that shows how much battery I have left?

Thanks

---

### Post by qamelian on 2011-11-25
> **molipha said:**
> Something that shows how much battery I have left?

Thanks
There should be one in the upper right corner of your display as part of the default configuration.

---

### Post by molipha on 2011-11-25
I didn't get one. There is:
- system settings,
- calendar,
- sound,
- wireless networks,
mail.

No power monitor

---

### Post by Jabra91 on 2011-11-25
you could use conky to do this

---

### Post by qamelian on 2011-11-25
That's weird, as the battery monitor *is* part of the default setup. I'm not sure what package provides it off the top of my head, but it is supposed to be installed by default. I'm pretty sure it's one of the indicator packages.

---

### Post by molipha on 2011-11-25
> **Jabra91 said:**
> you could use conky to do this

My first hit on conky included this:
Conky is an advanced, highly configurable system monitor for X based on  torsmo.Conky is an powerful desktop app that posts system monitoring  info onto the root window. It is hard to set up properly (has unlisted  dependencies, special command line compile options, and requires a mod  to xorg.conf to stop it from flickering, and the apt-get version doesnt  work properly). Most people can’t get it working right, but its an  AWESOME app if it can be set up right done.

Hmmm.

---

### Post by Frogs Hair on 2011-11-25
Some user seem to like Jupiter , unlike Conkey it has power settings . Conkey will only display information . [http://www.webupd8.org/2010/07/jupiter-ubuntu-ppa-hardware-and-power.html](http://www.webupd8.org/2010/07/jupiter-ubuntu-ppa-hardware-and-power.html)

---

### Post by Frogs Hair on 2011-11-25
> **molipha said:**
> My first hit on conky included this:
Conky is an advanced, highly configurable system monitor for X based on  torsmo.Conky is an powerful desktop app that posts system monitoring  info onto the root window. It is hard to set up properly (has unlisted  dependencies, special command line compile options, and requires a mod  to xorg.conf to stop it from flickering, and the apt-get version doesnt  work properly). Most people can’t get it working right, but its an  AWESOME app if it can be set up right done.

Hmmm.

The .conkyrc files usually have a buffering command in the syntax to reduce the flicker . This thread includes some useful links . [http://ubuntuforums.org/showthread.php?t=1397631](http://ubuntuforums.org/showthread.php?t=1397631)

---

