---
title: "AIM for ubuntu?"
date: 2011-06-01
forum: General Help
---

### Post by Zeoro on 2011-06-01
Anyone know why AIM isn't available for ubuntu? I don't like Pidgin,mostly because when an IM window is minimized and i receive a new message, it doesn't flash orange.

---

### Post by pqwoerituytrueiwoq on 2011-06-01
```
sudo apt-get remove indicator-messages
killall gnome-panel
```
then it shoud have pidgin's icon in your notification area since it no longer has the mail icon to hide under

---

