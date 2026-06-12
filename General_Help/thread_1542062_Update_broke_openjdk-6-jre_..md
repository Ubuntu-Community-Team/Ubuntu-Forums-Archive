---
title: "Update broke openjdk-6-jre ."
date: 2010-07-30
forum: General Help
---

### Post by mhwc on 2010-07-30
The update manager told me there were several packages to update, and I as usually said 'OK'. Then, it told me that some packages could not be installed. I ran dpkg in a terminal window, and this is what it looks like:

> sudo dpkg --configure -a                       
Setting up openjdk-6-jre-headless (6b18-1.8-4ubuntu3) ...
update-alternatives: error: alternative link /usr/bin/java is already managed by java~.
dpkg: error processing openjdk-6-jre-headless (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of openjdk-6-jre:
 openjdk-6-jre depends on openjdk-6-jre-headless (>= 6b18-1.8-4ubuntu3); however:
  Package openjdk-6-jre-headless is not configured yet.
dpkg: error processing openjdk-6-jre (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of icedtea-6-jre-cacao:
 icedtea-6-jre-cacao depends on openjdk-6-jre-headless (= 6b18-1.8-4ubuntu3); however:
  Package openjdk-6-jre-headless is not configured yet.
dpkg: error processing icedtea-6-jre-cacao (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of icedtea6-plugin:
 icedtea6-plugin depends on openjdk-6-jre (= 6b18-1.8-4ubuntu3); however:
  Package openjdk-6-jre is not configured yet.
dpkg: error processing icedtea6-plugin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 openjdk-6-jre-headless
 openjdk-6-jre
 icedtea-6-jre-cacao
 icedtea6-plugin

What is broken, and how can it be fixed?

---

### Post by igoddard on 2010-08-16
This now seems to be affecting Hardy.  There are allegedly 4 packages to update but require ca-certificates-java which is missing.  Debian repository has this package but trying to install it requires ca-certificates.  ca-certificates is installed but is older than Debian's version.

Does nobody test this stuff before they release it?

---

