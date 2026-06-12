---
title: "how can i change my remote desktop port in ubuntu 9.10 desktop"
date: 2009-12-14
forum: General Help
---

### Post by taimur on 2009-12-14
hi there,
how can i change my remote desktop port in ubuntu 9.10 desktop

thanks 
waiting for your reply

---

### Post by taimur on 2009-12-14
k

---

### Post by decoyoct on 2009-12-16
This is what helped me: 

[http://ubuntuforums.org/showthread.php?t=1165758](http://ubuntuforums.org/showthread.php?t=1165758)

but I didn't have to edit any xml files.

> **AlanB66 said:**
> (snip)

Open the Gnome Configuration Editor: gconf-editor

Proceed to **desktop -> gnome -> remote_access**

Place a check in the box for: **use_alternative_port**
Also, change the port to the value of your liking by double-clicking on **alternative_port **and changing the last two digits to any number between 01 and 99 (use two digit notation).

Close the Gnome Configuration Editor and re-try your VNC connection to the port you prefer (e.g.: jaunty:69)

---

