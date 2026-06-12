---
title: "How to install Nautilus Elementary"
date: 2010-08-11
forum: General Help
---

### Post by Audiosurfer on 2010-08-11
I want to install nautilus elementary but don't know how to do it. please help.

---

### Post by TheWeakSleep on 2010-08-11
Try this, open a terminal and type:
```
sudo add-apt-repository ppa:am-monkeyd/nautilus-elementary-ppa
```

```
sudo apt-get update && sudo apt-get upgrade
```

```
nautilus -q
```

that should work!

---

