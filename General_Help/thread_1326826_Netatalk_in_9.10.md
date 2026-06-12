---
title: "Netatalk in 9.10"
date: 2009-11-14
forum: General Help
---

### Post by davbeck on 2009-11-14
I installed Ubuntu 9.10 but when I went to setup Netatalk using: [http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/) I couldn't compile netatalk because of a dependency called lebcupsys2.

How do I get Netatalk compiled with SSL support?

---

### Post by davbeck on 2009-11-15
I found this resource: [http://geekfun.com/2009/10/18/fixing-upgrade-problems-with-netatalk-on-ubuntu-9-04-jaunty-jackelope/](http://geekfun.com/2009/10/18/fixing-upgrade-problems-with-netatalk-on-ubuntu-9-04-jaunty-jackelope/) that corrected the problem.

Basically, the new netatalk package doesn't require you to have a custom build but you have to change some settings from the old hack.

---

