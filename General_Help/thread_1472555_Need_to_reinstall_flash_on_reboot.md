---
title: "Need to reinstall flash on reboot"
date: 2010-05-04
forum: General Help
---

### Post by caffienefree on 2010-05-04
Hi all,

I have a bit of an odd bug, and I haven't been able to find a permanent solution so far. I recently upgraded from 9.10 to 10.04. After upgrading, flash seemed to stop working. 

I went to the adobe website, which prompted me to use the apturl to install adobe-flashplugin version 10.0.45.2-1lucid1. Flash worked fine after that. When I rebooted, flash stopped working. I removed and reinstalled flash, which seemed to work, until the next reboot. Repeat as necessary. 

Is there something that I'm missing? I tried to go back to the old version (flashplugin-nonfree) which didn't work at all. Any advice?

---

### Post by dino99 on 2010-05-04
i've no trouble here, i only use genuine packages: ubuntu-restricted-extras, flashplugin-installer

when things goes wrong, i'm used to remove/purge the packages then reinstall them

sudo apt-get install -f
sudo dpkg --configure -a

note: lot of users goes and downloaded third party packages, but remember that ubuntu devs fine tuned with ubuntu policy the packages, its not for nothing :o

---

