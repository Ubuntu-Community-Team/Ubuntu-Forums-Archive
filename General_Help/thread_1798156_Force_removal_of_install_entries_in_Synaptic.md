---
title: "Force removal of install entries in Synaptic"
date: 2011-07-06
forum: General Help
---

### Post by Packetbomb on 2011-07-06
I am using Ubuntu 10.04 LTS.

I have manually removed Canonicals version of coreutils (7.4-2ubuntu2) and installed the latest official version of coreutils (8.9).

Synaptic is still registering Canonicals version as being installed. Does anyone know how I can force remove the entry so it shows it as not being installed? I'm guessing there will be a file some where..

---

### Post by wildmanne39 on 2011-07-06
> **Packetbomb said:**
> I am using Ubuntu 10.04 LTS.

I have manually removed Canonicals version of coreutils (7.4-2ubuntu2) and installed the latest official version of coreutils (8.9).

Synaptic is still registering Canonicals version as being installed. Does anyone know how I can force remove the entry so it shows it as not being installed? I'm guessing there will be a file some where..Hi, open the terminal and use this command.
```
sudo apt-get --purge remove packagename
```

---

### Post by Elfy on 2011-07-06
Not usre if you can remove it as it's in the repositories, look into pinning for the newer version you have. 

[https://help.ubuntu.com/community/PinningHowto#Introduction%20to%20Holding%20Packages](https://help.ubuntu.com/community/PinningHowto#Introduction%20to%20Holding%20Packages)

---

### Post by mc4man on 2011-07-06
> I have manually removed 
Then there wouldn't be much to gain if synaptic recognizes this or not (it won't unless you installed the newer version as a deb package
Probably best to leave well enough alone
> 
Hi, open the terminal and use this command.
Code:

sudo apt-get --purge remove packagename

You really wouldn't want to do that with coreutils, though I doubt anyone would proceed after seeing what was to be uninstalled,  you never know though...

---

### Post by Packetbomb on 2011-07-06
> **wildmanne39 said:**
> Hi, open the terminal and use this command.
```
sudo apt-get --purge remove packagename
```

Thanks for your input dude, but the reason I want to manually remove it, is to stop it from removing everything that depends on it.
Like mc4man said, its trying to remove 2.5GB of other software which depends on coreutils.

If I can manually remove it, synaptic might just let be (though I doubt it).
My mission is to simply make synaptic not show it installed - as (7.4-2ubuntu2) no longer is. Know what I mean?


> **forestpiskie said:**
> Not usre if you can remove it as it's in the repositories, look into pinning for the newer version you have. 

[https://help.ubuntu.com/community/PinningHowto#Introduction%20to%20Holding%20Packages](https://help.ubuntu.com/community/PinningHowto#Introduction%20to%20Holding%20Packages)

Cool idea, but it doesn't work with installs made from source. coreutils' is released as source. I could make my own package, then pin it.. but what a drainer. lol


> **mc4man said:**
> Then there wouldn't be much to gain if synaptic recognizes this or not (it won't unless you installed the newer version as a deb package
Probably best to leave well enough alone

I can't stand faultiness. I might just uninstall synaptic. I am going building my own Linux system from scratch at the moment, so its probably best I start learning to live without package management systems sooner or later.


Thanks for all your help guy!!! :) :) :)

---

### Post by oldos2er on 2011-07-06
> **Packetbomb said:**
> Cool idea, but it doesn't work with installs made from source. coreutils' is released as source.  :) :) :)

Use checkinstall to create a deb package to install your source, then you can pin it. You'll need to uninstall coreutils first, of course. 

[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

---

