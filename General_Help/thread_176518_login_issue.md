---
title: "login issue"
date: 2006-05-14
forum: General Help
---

### Post by learning curve on 2006-05-14
When I login I get an error that says mu Home/.DRMC file has incorrect permissions.  Any Ideas?  I can just hit OK and it boots just fine, but it is irritating.

---

### Post by louis_nichols on 2006-05-14
just use

sudo chown <your username> ~/.dmrc

---

### Post by learning curve on 2006-05-14
did not work. i till get the error after login.

---

### Post by louis_nichols on 2006-05-15
oh! Sorry about that. Then, I recommend you delete it. Or, change it's name, in case you wanna take a look at it later. It will be recreated at login.

---

