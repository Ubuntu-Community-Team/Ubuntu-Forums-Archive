---
title: "where are 'other sources' stored?"
date: 2012-07-27
forum: General Help
---

### Post by Scooter_X on 2012-07-27
So, just trying to learn me a bit about the Debian package management system, I see that the main repos are in /etc/apt/sources.list, but then I got curious because I opened up my 'other sources' tab on 'software sources', because I'm not seeing any of those PPAs in the sources.list file - anyone know where list of those is?

---

### Post by Vaphell on 2012-07-27
check /etc/apt/sources.list.d/ dir
there are files one for each ppa

---

### Post by Scooter_X on 2012-07-27
That's it. Thanks a ton Vaphell!

---

