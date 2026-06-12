---
title: "Computer powered down during package update/installation. How to fix?"
date: 2009-11-14
forum: General Help
---

### Post by cknight on 2009-11-14
Long story short, last night I updated normal security and recommended updates via UpdateManager.  Unfortunately, the computer powered down during installation of the packages.  Upon reboot I have run:
```
sudo dpkg --configure -a
```
but get this output:
```
dpkg: dependency problems prevent configuration of icedtea-6-jre-cacao:
 icedtea-6-jre-cacao depends on openjdk-6-jre-headless (= 6b16-1.6.1-3ubuntu1); however:
  Version of openjdk-6-jre-headless on system is 6b16-1.6.1-1ubuntu3.
dpkg: error processing icedtea-6-jre-cacao (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 icedtea-6-jre-cacao

```

What's the best way to resolve this?  Thanks in advance.

---

### Post by cknight on 2009-11-14
Never mind.  Went into Synaptic Package Manager and selected Edit -> Fix Broken Packages.  This fixed the error above and from there was able to kick off the rest of the upgrade with 

```
sudo aptitude update && sudo aptitude safe-upgrade
```

---

