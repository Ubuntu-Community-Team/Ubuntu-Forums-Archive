---
title: "Repository Greyed Out"
date: 2011-12-21
forum: General Help
---

### Post by jim_deadlock on 2011-12-21
I have a package in my Update Manager that's greyed out, does this mean there's a problem with the repo and I should just remove it, or is it likely to fix itself or what? I've never seen this before.

[IMG]http://i932.photobucket.com/albums/ad168/jim_deadlock/dr3mro.gif[/IMG]

---

### Post by plucky on 2011-12-22
> **jim_deadlock said:**
> I have a package in my Update Manager that's greyed out, does this mean there's a problem with the repo and I should just remove it, or is it likely to fix itself or what? I've never seen this before.



The repository is still there.See [Here](http://ppa.launchpad.net/dr3mro/nautilus-actions-extra/ubuntu/dists/oneiric/main/)

It could be a dependency problem.What does ```
sudo apt-get dist-upgrade
``` show you from a terminal,.

---

### Post by jim_deadlock on 2011-12-22
```
The following packages have been kept back:
  nautilus-actions-extra
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```

---

### Post by plucky on 2011-12-22
Your installed version is 0.4.3~ppa1-0~46~oneiric1 whereas the newer version is 0.4.9~ppa1-0~oneiric1.

Why was it not updated before from the PPA? 

There have been a few versions previously uploaded.See [Here](https://launchpad.net/~dr3mro/+archive/nautilus-actions-extra/+builds?build_state=built)

I can see no reason why it hasn't updated before,and why it isn't updating now.Perhaps you can ask the person who maintains the PPA.

See [Here](https://launchpad.net/~dr3mro)

Or disable the PPA in Software Sources

Good Luck

---

