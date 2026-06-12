---
title: "Having trouble installing JRE 6u31"
date: 2012-04-06
forum: General Help
---

### Post by Vuxee on 2012-04-06
Hi everyone,

I am looking to install the latest JRE on my Ubuntu 11.04 box (32bit, using Xfce). I somehow managed to install a PPA repository which installed Java, however version 6u26 (I think), as this is my output for "java -version":

```
root@vuxee:~# java -version
java version "1.6.0_26"
Java(TM) SE Runtime Environment (build 1.6.0_26-b03)
Java HotSpot(TM) 64-Bit Server VM (build 20.1-b02, mixed mode)
```I have been looking around for a while now in an attempt to try and upgrade it to update 31, however I'm not in luck. Would anybody here know how to get rid of this outdated version and know how to install 6u31?

Thanks!

---

### Post by Karlchen on 2012-04-06
Hello, Vuxee.

Use Synaptic package manager to uninstall Java 1.6.0_26. Next comment out the PPA in your source.list.

Then visit this site and proceed as explained here step by step: [**Oracle (Sun) Java JRE for Ubuntu, Linux Mint and Debian**]("http://sites.google.com/site/easylinuxtipsproject/java#TOC-INSTALL-MANUALLY")

Good luck,
Karl

---

### Post by Vuxee on 2012-04-06
> **Karlchen said:**
> Hello, Vuxee.

Use Synaptic package manager to uninstall Java 1.6.0_26. Next comment out the PPA in your source.list.

Then visit this site and proceed as explained here step by step: [**Oracle (Sun) Java JRE for Ubuntu, Linux Mint and Debian**]("http://sites.google.com/site/easylinuxtipsproject/java#TOC-INSTALL-MANUALLY")

Good luck,
Karl

Thanks a lot Karl, that was easy to do and it worked out perfectly. :-)

---

### Post by Karlchen on 2012-04-07
Hello, Vuxee.

You're welcome. :) Great to learn that things went smoothly.

Cheers,
Karl

---

### Post by claracc on 2012-04-08
> Thanks a lot Karl, that was easy to do and it worked out perfectly

Please, mark the thread as solved with thread tools in the top right part of the page. Only who has started the thread can do.

---

