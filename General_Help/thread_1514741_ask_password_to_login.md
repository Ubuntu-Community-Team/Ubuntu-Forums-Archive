---
title: "ask password to login"
date: 2010-06-21
forum: General Help
---

### Post by DimitrisRHO on 2010-06-21
I can not make my ubuntu to ask password during login although the option of not to ask password is not ticked  :confused:

---

### Post by sisco311 on 2010-06-21
Is your user in the nopasswdlogin group? 
```
groups
```

If yes, then remove it from the group:
```
sudo gpasswd -d **user** nopasswdlogin
```
Replace **user** with your login name.

EDIT:
Or disable automatic login: System -> Administration -> Login Screen

---

