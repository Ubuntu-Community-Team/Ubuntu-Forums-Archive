---
title: "How do I downgrade Sun Java?"
date: 2011-02-24
forum: General Help
---

### Post by cscj01 on 2011-02-24
I had a performance problem with Sun Java 1.6.20 when running OOo Base some time back.  When I upgraded to 1.6.22 the problem was resolved.  The other day I upgraded to 1.6.24, and my performance problem is back.  So I would like to go back to 1.6.22.

Well, I found the debs for 1.6.22, used Synaptic to remove (complete removal) sun-java-jre and sun-java-bin.  Then I tried to install 1.6.22.  I got a message saying the package was broken.  If I respond to repair the package, 1.6.22 is upgraded to 1.6.24.  If I do not ask that the package be repaired, java does not work properly.

I also tried removal from a terminal using ```
apt-get purge
``` but the same thing happens.

I am at a loss here.  How do I completely remove 1.6.24 and install 1.6.22?

I am on Ubuntu 10.10.

---

### Post by cscj01 on 2011-02-24
Well, I figured out that if I removed Ubuntu Partners from my Sources list, I could get the version of Sun Java that came with Maverick.  So, I uninstalled sun-java6-bin and sun-java6-jre, unchecked the Partners source in Software Sources, installed sun-java6-bin and sun-java6-jre with Synaptic, and now have version 6.21dlj-0ubuntu1~maverick1~ppa1.  Best of all, my performance problem is gone.

---

### Post by ugm6hr on 2011-04-21
I think 1.6.21 is actually from the PPA - not the original canonical repo:
[http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu](http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu) maverick

---

