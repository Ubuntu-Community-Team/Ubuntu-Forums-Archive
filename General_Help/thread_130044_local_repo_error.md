---
title: "local repo error"
date: 2006-02-15
forum: General Help
---

### Post by shams2 on 2006-02-15
hi,
i make local repo /store/ubuntu/updates  from  the deb packages, and run the  script that created the:
Packages.gz
Sources.gz
added this entry to the /etc/apt/sources.list:
deb file:/store/ubuntu/ updates/
now when run the apt-get update this is the error:
Ign file: updates/ Release.gpg
Ign file: updates/ Release
Ign file: updates/ Packages

---

### Post by argusBR on 2006-04-11
I get the same message, but it doesn't seem to be a real error: if I run

sudo apt-get upgrade

it upgrades normally, using the packages from my local repo.

---

### Post by pacman^ on 2006-04-11
I have a feeling that the slash after word updates is too much. Have you tried removing it? If you want, I can post my /etc/apt/sources.list here...

---

