---
title: "Changing Name"
date: 2009-11-02
forum: General Help
---

### Post by ceo@jeetgroup.com on 2009-11-02
Hi,

I wish to change the name of the OS from ubuntu to DESAI. I mean everywhere the name displayed should be DESAI starting from the loading screen to shut down. Can i do that. If yes than HOW ?

Regards
Desai

---

### Post by klemes on 2009-11-02
edit the hostname by giving 
```
sudo nano /etc/hostname
```
in the console,followed by:
```
sudo /etc/init.d/networking restart
```
Cheers!!

---

