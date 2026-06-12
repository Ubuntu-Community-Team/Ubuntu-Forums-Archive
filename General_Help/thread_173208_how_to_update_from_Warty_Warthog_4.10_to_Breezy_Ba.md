---
title: "how to update from Warty Warthog 4.10 to Breezy Badger 5.10 Release"
date: 2006-05-10
forum: General Help
---

### Post by linuxlah on 2006-05-10
Do I need to reinstall of just aptitude world or something?

---

### Post by dickohead on 2006-05-10
You can do both :)

1. - Edit your /etc/apt/sources.list file and change each line where it says warty to breezy, then run,
sudo apt-get update
sudo apt-get dist-upgrade

2. - Backup things you don't want to lose (network or CD/DCD) and then just boot from the install disc.


I upgraded from warty to breezy and it went pear shaped in some areas, so if you have issues after an update, the install will work better.

---

### Post by nocturn on 2006-05-10
dist-upgrading is not recommended when you skip releases.  It can give all sorts of problems unless the devs handle it, which is not the case for Ubuntu.

---

### Post by dickohead on 2006-05-10
That would be why mine went all screwy!

Perhaps you could go from Warty to Hoary to Breezy?

---

