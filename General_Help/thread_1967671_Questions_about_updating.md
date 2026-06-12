---
title: "Questions about updating"
date: 2012-04-28
forum: General Help
---

### Post by 0011235813 on 2012-04-28
Hi, I noticed 12.04 is now available. I would like to ask some questions regarding upgrades through update manager, and whether there are any issues I should be aware of.

First, I have an encrypted home directory. Will this affect upgrading? I will backup all my files just in case, but I'm asking, will it keep my files encrypted, or will it decrypt them? It'd be nice if I have an unencrypted swap so I don't have to worry about hibernate.

Secondly, I have two users on the computer. Will the users remain the same?

Third, I have multiple interfaces installed. I prefer Gnome 3.2 or 3.4 over Unity. Will I have to reinstall these interfaces?

Fourth, settings. Will my settings be kept?

Finally, programs. Will I keep the programs I have installed? What about external repositories?

Any answers would be appreciated.

---

### Post by K4NEB on 2012-04-28
all ill say is wait a month for little niggles to be ironed out, thenm upgrade.

---

### Post by 0011235813 on 2012-04-28
Has anyone ever used update manager to upgrade to a newer version of Ubuntu?

---

### Post by jerome1232 on 2012-04-28
> **0011235813 said:**
> 
First, I have an encrypted home directory. Will this affect upgrading? I will backup all my files just in case, but I'm asking, will it keep my files encrypted, or will it decrypt them? It'd be nice if I have an unencrypted swap so I don't have to worry about hibernate.
It will stay encrypted, won't change

> **0011235813 said:**
> 
Secondly, I have two users on the computer. Will the users remain the same?
Users will remain the same

> **0011235813 said:**
> 
Third, I have multiple interfaces installed. I prefer Gnome 3.2 or 3.4 over Unity. Will I have to reinstall these interfaces?
Gnome-shell should stay there. The upgrade process will tell you what packages it intends to remove and you can look the the list before committing to the upgrade to double check.

> **0011235813 said:**
> 
Fourth, settings. Will my settings be kept?


Kind of, some preferences my change if they are depreciated etc.... For instance my backgrounds changed, a few other misc settings changed.

> **0011235813 said:**
> 
Finally, programs. Will I keep the programs I have installed? What about external repositories?

All external repos will be disabled, all programs will be kept except the ones included in the list of packages that need to be removed as mentioned earlier.

---

### Post by ubuntu27 on 2012-04-28
When upgrading, Ubuntu will try to keep your old settings intact.

This has PROS and COS.

The PRO is that you keep your old settings, so there is nothing that you might dislike.

The CONS is that perhaps, the old configuration is not ¨adequate¨ or interferes with the new version of a program. (File, configuration corruption). 


How successful your upgrade will be depends on your hardware and the mix of software that you have installed. So the mileage varies.

See:

[Ubuntu 10.04 – 12.04 Upgrade – How Well Does it Go?]("http://admin.omgubuntu.co.uk/2012/04/ubuntu-10-04-12-04-upgrade-how-well-does-it-go/")

---

