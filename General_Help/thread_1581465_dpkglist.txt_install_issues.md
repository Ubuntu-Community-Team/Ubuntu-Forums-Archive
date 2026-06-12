---
title: "dpkglist.txt install issues"
date: 2010-09-25
forum: General Help
---

### Post by sr_guy on 2010-09-25
Ran this to backup my app list:

dpkg --set-selections < /tmp/dpkglist.txt

After install a fresh copy of 10.04, I tried to run this command after running apt-get update & apt-get upgrade:

apt-get dselect-upgrade


Unfortunately, it to restore ant of my previous apps that were in that list. Whatwould be the reason for this? I thought that dselect-upgrade was supposed to install anything in the dpkglist.txt list?

---

### Post by sr_guy on 2010-09-25
I figured it out :)


Run this command as root where dpkglist.txt is stored:

dpkg --set-selections < dpkglist.txt && sudo apt-get dselect-upgrade

---

