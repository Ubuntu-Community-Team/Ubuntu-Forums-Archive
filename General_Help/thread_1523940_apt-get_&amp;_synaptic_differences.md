---
title: "apt-get &amp; synaptic differences"
date: 2010-07-04
forum: General Help
---

### Post by MooPi on 2010-07-04
I use openbox on most of my systems and I use terminal apt-get for package management. My quandary is why is there a difference in how these two handle linux-generic linux-headers-generic linux-image-generic. When I use ```
apt-get upgrade
``` it holds these back and if I use Synaptic and mark all upgrades it installs all three. I've searched through the man pages and help files for apt-get for a reason and drawn a blank.

---

### Post by philinux on 2010-07-04
> **MooPi said:**
> I use openbox on most of my systems and I use terminal apt-get for package management. My quandary is why is there a difference in how these two handle linux-generic linux-headers-generic linux-image-generic. When I use ```
apt-get upgrade
``` it holds these back and if I use Synaptic and mark all upgrades it installs all three. I've searched through the man pages and help files for apt-get for a reason and drawn a blank.

In that situation from a terminal you would use dist-upgrade which is what synaptic will do.

Other alternative is

sudo aptitude update && sudo aptitude safe-upgrade or full-upgrade

---

### Post by MooPi on 2010-07-04
Lets suppose I'm using version 9.10 and use the command ```
apt-get dist-upgrade
```
Won't I end up with and upgrade to 10.04 ? which isn't what I'm shooting for.

---

### Post by philinux on 2010-07-04
> **MooPi said:**
> Lets suppose I'm using version 9.10 and use the command ```
apt-get dist-upgrade
```
Won't I end up with and upgrade to 10.04 ?

No that would be ```
update-manager -d
```


> dist-upgrade
           dist-upgrade in addition to performing the function of upgrade, also intelligently [B]handles changing
           dependencies with new versions of packages[/B]; apt-get has a "smart" conflict resolution system, and it will
           attempt to upgrade the most important packages at the expense of less important ones if necessary. So,
           dist-upgrade command may remove some packages. The /etc/apt/sources.list file contains a list of locations from
           which to retrieve desired package files. See also apt_preferences(5) for a mechanism for overriding the general
           settings for individual packages.


---

