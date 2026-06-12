---
title: "package installation interrupted"
date: 2010-06-11
forum: General Help
---

### Post by sites on 2010-06-11
When installing build-essential and ubuntu-restricted-extras the internet connection was interrupted.  How can I force re-installation in terminal?  I'm looking all over for the commands but i can't find them.  If i just type "sudo apt-get install build-essential ubuntu-restricted-extras" it returns the message that they are both up to date.  I know one of them was interrupted and needs to be finished.  Thanks

---

### Post by oldos2er on 2010-06-11
```
sudo dpkg --configure -a
```

---

