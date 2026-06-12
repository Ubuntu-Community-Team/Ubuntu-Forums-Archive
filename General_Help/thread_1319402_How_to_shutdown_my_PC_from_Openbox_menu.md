---
title: "How to shutdown my PC from Openbox menu ?"
date: 2009-11-08
forum: General Help
---

### Post by Somme on 2009-11-08
```
sudo shutdown -h now

```It works if I use it in Terminal but the problem is that the menu will not ask me for a password. 
How do I shutdown my PC without a password or at least get a prompt when I need to enter it ?

---

### Post by shaon3343 on 2009-11-08
hi there, 
I think this could help you: [http://ubuntuforums.org/showthread.php?t=1276390](http://ubuntuforums.org/showthread.php?t=1276390)

---

### Post by Somme on 2009-11-08
> **shaon3343 said:**
> hi there, 
I think this could help you: [http://ubuntuforums.org/showthread.php?t=1276390](http://ubuntuforums.org/showthread.php?t=1276390)

```
%admin ALL=NOPASSWD: /sbin/shutdown
```

Thank you - problem solved.

---

