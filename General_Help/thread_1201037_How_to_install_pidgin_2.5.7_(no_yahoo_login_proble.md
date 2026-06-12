---
title: "How to install pidgin 2.5.7 (no yahoo login problem)"
date: 2009-06-30
forum: General Help
---

### Post by colau on 2009-06-30
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8

echo deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu `lsb_release --short --codename` main | sudo tee /etc/apt/sources.list.d/pidgin-ppa.list

sudo apt-get update

sudo apt-get upgrade

```

---

