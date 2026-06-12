---
title: "adding ppa via software centre - untrusted packages"
date: 2011-12-12
forum: General Help
---

### Post by ELD on 2011-12-12
Okay guys is there any reason why when I add a ppa via ubuntu software centre that when i try to then update from that ppa update manager throws a hissy fit saying its not authenticated?

I thought USC was supposed to auto-get the authentication keys?

---

### Post by satanselbow on 2011-12-12
You can add the keys after the event - although I agree it should do it automatically
 
to add ppa key:
 
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys XXXXXXXX
```
 
XXXXXXXX is either the 2nd  part of the signing key ie 1024R/**72D340A3**
or the 40(?) digit key hash

---

