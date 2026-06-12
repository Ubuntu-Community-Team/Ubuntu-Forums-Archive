---
title: "security update"
date: 2006-04-10
forum: General Help
---

### Post by RajivNair on 2006-04-10
i have ubuntu 5.10 installed on my pc for 2 months now but have never patched any security updates.can anyone plz tell me as to how to patch up security updates for ubuntu 5.10 till date.

---

### Post by Darkriser on 2006-04-10
edit your sources (sudo gedit /etc/apt/sources.list) following:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-security main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-security main restricted universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe

and run in console:
sudo apt-get update
sudo apt-get upgrade

---

### Post by nocturn on 2006-04-10
Configure update-manager from the Administration menu.

---

### Post by RajivNair on 2006-04-10
thank you darkriser and nocturn for your kindly help.

---

