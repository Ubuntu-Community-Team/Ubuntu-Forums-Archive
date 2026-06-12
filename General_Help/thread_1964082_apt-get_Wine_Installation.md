---
title: "apt-get: Wine Installation"
date: 2012-04-23
forum: General Help
---

### Post by Novus Anima on 2012-04-23
Earlier today before school I was attempting to install Wine through the Ubuntu Software Center. The installation was completely stalled because it was waiting for some apt-get to exit. Not 100% sure why apt-get is open, nor am I positive how to close it, but I apparently need it closed in order to install Wine.

Anyone know why apt-get is restricting my installation?

---

### Post by techsupport on 2012-04-23
> **Novus Anima said:**
> Earlier today before school I was attempting to install Wine through the Ubuntu Software Center. The installation was completely stalled because it was waiting for some apt-get to exit. Not 100% sure why apt-get is open, nor am I positive how to close it, but I apparently need it closed in order to install Wine.

Anyone know why apt-get is restricting my installation?

What I would do is reboot, and try installing Wine from the PPA instead.  Maybe try installing PlayOnLinux from the PPA too.  You can find those here:

[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

---

### Post by oldfred on 2012-04-23
I have had synaptic open and tried running and apt-get and it would not work as you cannot have two applications doing the same at the same time. There is a lock file somewhere but I do not know where.

Did you have another application open like synaptic or something that would lock installer.

---

### Post by techsupport on 2012-04-23
> **oldfred said:**
> I have had synaptic open and tried running and apt-get and it would not work as you cannot have two applications doing the same at the same time. There is a lock file somewhere but I do not know where.

Did you have another application open like synaptic or something that would lock installer.

It could also be that they have automatic updates enabled.

---

