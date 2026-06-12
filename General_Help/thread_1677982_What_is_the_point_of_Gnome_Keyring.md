---
title: "What is the point of Gnome Keyring ?"
date: 2011-01-29
forum: General Help
---

### Post by alket on 2011-01-29
Besides that annoys you every time you start Ubuntu, asks for password several times etc. If it is for some kind of security its easily hacked by
```
rmdir .gnome2/keyrings
```
restart the machine and it is rested.

So why do we use it ? What is the purpose ?

---

### Post by kidders on 2011-01-30
Hi there,

I'm not sure how deleting keyrings creates a security problem. :confused: If anything, surely it would have the opposite effect.

You might be interested in [http://live.gnome.org/GnomeKeyring/SecurityFAQ](http://live.gnome.org/GnomeKeyring/SecurityFAQ). The point is to protect your passwords from prying eyes so if, for example, your machine is compromised, there's at least *some* level of difficulty attached to using it as a means of gaining access to other systems you may have logged into.

I hope that helps.

---

### Post by alket on 2011-01-30
By deleting the gnome keyring folder, the keyring is rested and asks for new password on login.

---

### Post by gradinaruvasile on 2011-01-30
The whole idea is to protect your saved passwords - if you delete it, you will lose all passwords stored in it.
The fact that it can be erased is not "security issue" because no information is gained from it about the saved passwords.
BTW never ever rely on the computer to remember your passwords instead of you.

---

