---
title: "Skype permisssion."
date: 2009-12-29
forum: General Help
---

### Post by dilshannet on 2009-12-29
[I]
 I installed and ran skype as a root user (first time). i no longer can sign in to skype as a normal user. Pls provide me a solution. [/I]

---

### Post by sisco311 on 2009-12-29
Open a terminal and run:
```
sudo chown -R $USER\: ~/.Skype
```

If you have to run a GUI application as root use gksu.
[http://psychocats.net/ubuntu/graphicalsudo]("http://psychocats.net/ubuntu/graphicalsudo")

---

### Post by 3rdalbum on 2009-12-29
Don't run Internet-facing programs as root.

---

