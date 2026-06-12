---
title: "Where's a nice place to put scripts to be run by cron?"
date: 2010-07-22
forum: General Help
---

### Post by Vunutus on 2010-07-22
I'm not using the anacron folders like cron.daily and such so I'm not just plopping them in there. I'm using cron.d so I have more control over when my scripts are run. I currently have them just sitting in my home directory but this isn't really ideal since they're system-wide scripts .

Where in my file system should I put these scripts to be run by cron?

---

### Post by gdonwallace on 2010-07-22
You will have to edit crontab so it hits the right directory, but I would suggest /opt.  Whenever I have anything automated or a third party software installed, I put it there.  

The advantage is that everything that I install or write a script for is in a single directory.  And the biggest advantage is the /opt does not get touched during distro upgrades.  So anything that is put in the /opt directory stays when you **upgrade** from one version to the next.

---

