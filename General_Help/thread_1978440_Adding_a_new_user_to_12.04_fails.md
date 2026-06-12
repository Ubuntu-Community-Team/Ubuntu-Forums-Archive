---
title: "Adding a new user to 12.04 fails"
date: 2012-05-11
forum: General Help
---

### Post by CujoQuarrel on 2012-05-11
New installation of Ubuntu 12.04. 

I can add a new user but when ever I log into that account it just throws me back to the login screen. I used the graphical interface Administration->Users and Groups

Any help would be appreciated.

---

### Post by mc4man on 2012-05-11
Users and Groups isn't used anymore so some things may work in it, some may not 

Try opening User Accounts in System Settings or from terminal
```
gnome-control-center user-accounts
```
If your new user is there then remove & re-create, if not there then create, ect.

---

