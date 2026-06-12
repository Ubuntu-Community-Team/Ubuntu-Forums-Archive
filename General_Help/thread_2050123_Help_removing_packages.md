---
title: "Help removing packages"
date: 2012-08-30
forum: General Help
---

### Post by justinesmithies on 2012-08-30
I installed on Ubuntu 12.04 clamav-daemon clamav etc then removed it. I stupidly removed the users manually and the /etc/clamav directory.
Now i cannot get clamav clamav-daemon to install as it does not create the users and groups and cannot create the /etc/clamav/ files / directory

Can someone please help as i need to get it reinstalled.

---

### Post by SlugSlug on 2012-08-30
sudo apt-get purge clamav-daemon clamav

sudo apt-get install clamav-daemon clamav


if not then

sudo apt-get install aptitude

sudo aptitude reinstall clamav-daemon clamav

---

