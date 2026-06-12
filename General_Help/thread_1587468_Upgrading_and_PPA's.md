---
title: "Upgrading and PPA's"
date: 2010-10-03
forum: General Help
---

### Post by baddnady23 on 2010-10-03
I have my home on a separate partition from /.  When 10.10 comes out I will simply upgrade from the Live disc to the new version and keep my home.  Question is, I have several PPA's that I am using for keep several programs updates.  How will I be able to keep these PPA's through the upgrade process, since I have no idea where I got them from over the past year.  I thought that with each upgrade the sources.list gets upgraded as well and you need to add all the repositories again...  Thanks!

---

### Post by oldos2er on 2010-10-03
You probably should disable the PPAs before upgrading, and re-enable them afterwards, remembering to change any instances of "lucid" to "maverick." Copy your current /etc/apt/sources.list and/or the contents of /etc/apt/sources.list.d to your /home/user folder.

---

### Post by baddnady23 on 2010-10-03
My upgrade will bea fresh install from cd... do I still need to disable PPAs?

---

### Post by andrewthomas on 2010-10-03
Fresh install = no ppa. Nothing to disable

---

