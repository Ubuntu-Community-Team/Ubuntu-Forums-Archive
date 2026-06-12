---
title: "AMD64 - What should I do after a crash and a hard reset?"
date: 2010-10-25
forum: General Help
---

### Post by synergie on 2010-10-25
Hi there,

After my computer freezes, and I have to do a hard reset (holding the power button) or removing the battery, What should I do? De fragment? something ?

Thanks everyone!

---

### Post by ironic.demise on 2010-10-25
> **synergie said:**
> Hi there,

After my computer freezes, and I have to do a hard reset (holding the power button) or removing the battery, What should I do? De fragment? something ?

Thanks everyone!

Ubuntu doesn't need defragmenting.
```
sudo apt-get update
sudo apt-get cleanup
sudo apt-get upgrade
```

... or try re-installing 32 bit if it's a 64 bit driver issue?

---

### Post by AlphaLexman on 2010-10-25
What to do when and if your linux system freezes up: [http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

---

### Post by synergie on 2010-10-26
> **ironic.demise said:**
> Ubuntu doesn't need defragmenting.
```
sudo apt-get update
sudo apt-get cleanup
sudo apt-get upgrade
```... or try re-installing 32 bit if it's a 64 bit driver issue?


Naw it's just me screwin around, messing with settings, etc... 

what does the cleanup do?

---

### Post by dcstar on 2010-10-26
> **synergie said:**
> Naw it's just me screwin around, messing with settings, etc... 

what does the cleanup do?

Waste more of your time since they have nothing to do with your resets, unless you believe that tidying up your installed packages is worth your while.

---

### Post by ironic.demise on 2010-10-26
> **dcstar said:**
> Waste more of your time since they have nothing to do with your resets, unless you believe that tidying up your installed packages is worth your while.

Cleanup removes old unnecessary packages from your PC, I just figured if you had the latest upgrade there might be a few bug fixes that might have been causing some trouble.

---

