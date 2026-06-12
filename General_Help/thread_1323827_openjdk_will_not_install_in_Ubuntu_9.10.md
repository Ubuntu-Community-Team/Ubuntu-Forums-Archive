---
title: "openjdk will not install in Ubuntu 9.10"
date: 2009-11-12
forum: General Help
---

### Post by Terrycymru on 2009-11-12
Following an upgrade from 9.04 to 9.10 I decided to uninstall sun java and install openjdk-6-jre using Synaptic but it failed reporting these errors:

Depends: openjdk-6-jre headless but it is not going to be installed

Depends: libaccess-bridge-java-jni but it is not going to be installed

When I try to install the dependencies I get into a loop of missing dependencies. What is wrong?

**LATER: [SOLVED] See #6 below for later information.**

---

### Post by bashphoenux on 2009-11-12
you have to install 
-openjdk-6-jre headless 
-openjdk-6-jre-lib
-libaccess-bridge-java-jni
libaccess-bridge-java
the above for installing openjdk so mark each one of the above in synaptic and then try

---

### Post by Terrycymru on 2009-11-12
When I try to mark a package (for example openjdk-6-jre-headless) I get this error:

Could not mark all packages for installation or upgrade

openjdk-6-jre-headless:
 Depends: openjdk-6-jre-lib but it is not going to be installed
 Depends: ca-certificates-java but it is not going to be installed
 Depends: tzdata-java but it is not going to be installed
 Depends: rhino but it is not going to be installed
 Recommends: icedtea-6-jre-cacao but it is not going to be installed

This is what I meant when I said I get into a loop.

rhino wants to install dependencies including sun-java !!

tzdata-java complains:
tzdata-java:
  Depends: tzdata (=2009o-1ubuntu2) but 2009o+repack-0ubuntu0.9.04.2 is to be installed.

Problem may be that tzdata-java does not accept latest version of tzdata. Sounds like a bug in the tzdata-java offered by the repositories.

---

### Post by Terrycymru on 2009-11-12
I have reported this as Bug #481194. 

A recent Debian bug is titled " Recent upgrade of tzdata leads to broken tzdata-java package" so is it an upstream issue?

But in Ubuntu 9.10 there is the additional issue why is rhino seeking to install sun-java?

---

### Post by Terrycymru on 2009-11-12
There is a workaround for this bug at Bug 241268 #10 for anyone who has suffered this problem after a Jaunty to Karmic upgrade.

Before you try to install openjdk-6-jre:

WORKAROUND for Jaunty to Karmic upgrade:
sudo apt-get install tzdata=2009o-1ubuntu2
and say Y to "downgrade"

---

### Post by Terrycymru on 2009-11-14
Update Manager has now offered updates to tzdata and tzdata-java (both version 2009r-0ubuntu9.10) which should make the above workaround unnecessary. Make sure you have updated tzdata and tzdata-java before you try to install openjdk.

---

