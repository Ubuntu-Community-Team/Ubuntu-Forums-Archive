---
title: "Pidgin shows wrong version (2.5.5. instead of 2.6.5.)"
date: 2010-01-16
forum: General Help
---

### Post by Daniel_le_Rouge on 2010-01-16
Hello!

I have a problem with using the developers' version of Pidgin which is version 2.6.5.

I added the correct ppa to my sources.list and updated normally. Everything seems to work all right. This is the version Synaptics is showing:

```
daniel@daniel-laptop:~$ apt-cache policy pidgin
pidgin:
  Installiert: 1:2.6.5-0ubuntu1~pidgin1.9.10
  Kandidat: 1:2.6.5-0ubuntu1~pidgin1.9.10
  Versions-Tabelle:
 *** 1:2.6.5-0ubuntu1~pidgin1.9.10 0
        500 http://ppa.launchpad.net karmic/main Packages
        100 /var/lib/dpkg/status
     1:2.6.2-1ubuntu7 0
        500 http://de.archive.ubuntu.com karmic/main Packages

```

But when I look up the version in Pidgin itself, it tells that it is version 2.5.5. and when I ask for updates it wants me to download version 2.6.5.

What is wrong with the program and how can I solve the problem?

Thanks!

Daniel

---

