---
title: "Impossible uninstall &quot;Password Safe&quot;"
date: 2012-08-10
forum: General Help
---

### Post by davidgv on 2012-08-10
I've installed the program "Password Safe" from [http://sourceforge.net/projects/passwordsafe/files/Linux-BETA/0.8.0/](http://sourceforge.net/projects/passwordsafe/files/Linux-BETA/0.8.0/)
but now I can't uninstall it.

Don't exists in Software Center, and if I make 
```
sudo apt-get purge pwsafe
```
the system tell me that the packet isn't installed.

What can I do to uninstall it?

---

### Post by unevenflow on 2012-08-10
if you installed a deb package then
sudo apt-get install synaptic
and from there search for this program and click for complete removal.

---

### Post by davidgv on 2012-08-10
It's correct. Thank you.

---

