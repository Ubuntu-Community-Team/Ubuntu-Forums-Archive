---
title: "Desktop Sharing Preferences"
date: 2012-08-20
forum: General Help
---

### Post by kuvanito on 2012-08-20
does any one here knows how to remove this application from ubuntu?
thank you.

---

### Post by vandorjw on 2012-08-21
No idea. why do you want it gone?

Here is something that might set you on the right track

dpkg -l (list all installed packages)

dpkg -l | grep remote (list all installed packages containing the word remote)


sudo apt-get purge "whatever you found"

sudo apt-get purge openssh-server

---

