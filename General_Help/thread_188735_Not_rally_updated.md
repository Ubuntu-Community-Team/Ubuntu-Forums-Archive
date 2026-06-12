---
title: "Not rally updated"
date: 2006-06-04
forum: General Help
---

### Post by Xell on 2006-06-04
Hi

I tried to do the update from breezy to dapper by editing the sources.list (changing breezy to dapper) and doing the sudo apt-get update and sudo apt-get upgrade, but the menue has not changed and I didn't get the new shutdown dialog. How can I make sure I get all the new features?

---

### Post by simplyw00x on 2006-06-04
You do 
sudo apt-get dist-upgrade

---

### Post by OffHand on 2006-06-04
```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by eqisow on 2006-06-04
I third what the guys above said. Also, doing a simple apt-get upgrade when going from one version to another is very dangerous. You're lucky anything is working at all. ;)

---

### Post by Xell on 2006-06-04
I might be bad at explaining, but thats exactly what I did. And now it says all is up to date only the manue is still the old one and so is the shut-down dialog. So it doesn't seem to be quite upgraded.

Any other ideas?

edit: sorry, I saw my typo now. I did mean I did the sudo apt-get dist-upgrade.

---

