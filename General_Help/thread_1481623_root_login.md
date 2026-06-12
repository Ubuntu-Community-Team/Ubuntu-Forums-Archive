---
title: "root login"
date: 2010-05-12
forum: General Help
---

### Post by dbassett on 2010-05-12
terminal login as root. I do su root and then password but I get auth failed. I'm the only user and I'm part of the root main group.
How do I login to terminal as root?

---

### Post by dbassett on 2010-05-12
Ah I got it
sudo -i

---

### Post by Iowan on 2010-05-12
More details than you probably need:
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by skibum3027 on 2010-05-12
The short version of the story is that ubuntu doesn't use the root user the same way most linux based distros do. Instead of logging into root user, you simply put sudo in front of terminal commands, gksudo for apps in GNOME, and kdesudo for apps in KDE.

---

