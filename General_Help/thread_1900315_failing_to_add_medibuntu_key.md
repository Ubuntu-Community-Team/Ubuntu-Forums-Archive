---
title: "failing to add medibuntu key"
date: 2011-12-26
forum: General Help
---

### Post by jon zendatta on 2011-12-26
As the error says I can't connect to medibuntu.
```
sudo -E wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
--2011-12-27 07:25:51--  http://www.medibuntu.org/sources.list.d/oneiric.list
Resolving www.medibuntu.org... 1.0.0.0
Connecting to www.medibuntu.org|1.0.0.0|:80... 
```
and trying to install ubuntu-restricted-extras similar problem

--2011-12-27 07:57:24--  [http://downloads.sourceforge.net/corefonts/andale32.exe](http://downloads.sourceforge.net/corefonts/andale32.exe)
Resolving downloads.sourceforge.net... 1.0.0.0
Connecting to downloads.sourceforge.net|1.0.0.0|:80...

---

### Post by jon zendatta on 2011-12-26
fixed. end of story

---

