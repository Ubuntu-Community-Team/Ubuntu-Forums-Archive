---
title: "Post-install problems with apt"
date: 2006-05-18
forum: General Help
---

### Post by elver on 2006-05-18
I installed 5.10 on my work computer here. Apt screwed up at the end of the installation and told me that it'd work out problems with unconfigured packages later.

Now, every time I install something with apt, I get such a pile of error messages at the end:

dpkg: dependency problems prevent configuration of openoffice.org2-common:
 openoffice.org2-common depends on openoffice.org2-core (>> 1.9.129); however:
  Package openoffice.org2-core is not configured yet.
 openoffice.org2-common depends on openoffice.org2-l10n-en-us (>= 1.9.129); however:
  Package openoffice.org2-l10n-en-us is not configured yet.
dpkg: error processing openoffice.org2-common (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gij-4.0
 gij
 libgnujaxp-java
 libjessie-java
 java-gcj-compat
 libgnucrypto-java
 bsh
 eclipse-base
 libservlet2.3-java
 libhsqldb-java
 libjaxp1.2-java
 libxerces2-java
 libxalan2-java
 libxt-java
 openoffice.org2-java-common
 openoffice.org2-core
 openoffice.org2-l10n-en-us
 python-uno
 openoffice.org2-writer
 openoffice.org2-calc
 openoffice.org2-draw
 openoffice.org2-impress
 openoffice.org2-math
 openoffice.org2-base
 openoffice.org2
 openoffice.org2-evolution
 openoffice.org2-gnome
 ubuntu-desktop
 zope-backtalk
 zope-callprofiler
 openoffice.org2-common
E: Sub-process /usr/bin/dpkg returned an error code (1)

Has anyone else encountered this and how do I fix it?

---

### Post by lukew on 2006-05-18
[QUOTE=elver]I installed 5.10 on my work computer here. Apt screwed up at the end of the installation and told me that it'd work out problems with unconfigured packages later.

Now, every time I install something with apt, I get such a pile of error messages at the end:

dpkg: dependency problems prevent configuration of openoffice.org2-common:
 openoffice.org2-common depends on openoffice.org2-core (>> 1.9.129); however:
  Package openoffice.org2-core is not configured yet.
 openoffice.org2-common depends on openoffice.org2-l10n-en-us (>= 1.9.129); however:
  Package openoffice.org2-l10n-en-us is not configured yet.
dpkg: error processing openoffice.org2-common (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gij-4.0
 gij
 libgnujaxp-java
 libjessie-java
 java-gcj-compat
 libgnucrypto-java
 bsh
 eclipse-base
 libservlet2.3-java
 libhsqldb-java
 libjaxp1.2-java
 libxerces2-java
 libxalan2-java
 libxt-java
 openoffice.org2-java-common
 openoffice.org2-core
 openoffice.org2-l10n-en-us
 python-uno
 openoffice.org2-writer
 openoffice.org2-calc
 openoffice.org2-draw
 openoffice.org2-impress
 openoffice.org2-math
 openoffice.org2-base
 openoffice.org2
 openoffice.org2-evolution
 openoffice.org2-gnome
 ubuntu-desktop
 zope-backtalk
 zope-callprofiler
 openoffice.org2-common
E: Sub-process /usr/bin/dpkg returned an error code (1)

Has anyone else encountered this and how do I fix it?[/QUOTE]
Hi,

I had this with some elisp package, the other day. I uninstalled the package, which it allowed me to do even thought it was not installed, and the problem went away.

It looks like it caches the deb files it has downloaded and tries to instal them again and again untill sucessful.

I hope this helps.

Luke

---

