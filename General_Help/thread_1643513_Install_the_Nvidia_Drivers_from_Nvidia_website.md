---
title: "Install the Nvidia Drivers from Nvidia website"
date: 2010-12-12
forum: General Help
---

### Post by thebarisaxkid on 2010-12-12
Sup,

I have Ubuntu 10.10.  I want to install the from the nvidia website.  The propriatary drivers from Ubuntu aren't great.  I have downloaded the file, but what do I do with it now?  How can I get it installed?

Thanks!

---

### Post by Rodney9 on 2010-12-12
Search is your friend 

[http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia](http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia)

---

### Post by cascade9 on 2010-12-12
What do you mean by "The propriatary drivers from Ubuntu aren't great"? 

I doubt you'll notice much difference, if any at all between the drivers in the repos and the ever so slightly newer drivers from the nvidia site.

---

### Post by FreezWay on 2010-12-12
DON'T. they are very likely to break stuff. I've been there before, its not a great place to be. The default drivers (under proprietary drivers) seem to work fine, but if you really must, i recommended the drivers [here]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates")

---

### Post by thebarisaxkid on 2010-12-12
> **FreezWay said:**
> DON'T. they are very likely to break stuff. I've been there before, its not a great place to be. The default drivers (under proprietary drivers) seem to work fine, but if you really must, i recommended the drivers [here]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates")

hmm, those drivers look interesting.  How can I download/install them?

---

### Post by Krytarik on 2010-12-13
> **thebarisaxkid said:**
> hmm, those drivers look interesting.  How can I download/install them?
Altough I also the proprietary Nvidia-drivers packaged by Ubuntu, to install those drivers enter in a terminal:```

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
```
Personally I would always do the actual upgrade/installation via Synaptic, it's much more userfriendly and transparent imo. To upgrade this way go to "System -> Administration -> Synaptic Package Manager" and (after entering your root-password) select "Mark All Upgrades", then "Apply".

Please tell me if there is a significant improvement whith those drivers!

---

