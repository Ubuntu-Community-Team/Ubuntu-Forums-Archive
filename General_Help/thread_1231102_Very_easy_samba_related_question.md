---
title: "Very easy samba related question"
date: 2009-08-04
forum: General Help
---

### Post by Blundey on 2009-08-04
Hi guys,

Ive setup a samba share in gnome and its working great. However I want to write a script to make other shares via the console. 

The problem is I cant find where gnomes GUI has written the share information to. Ive checked /etc/smb.conf and there is no mention of the shares I have created on the GUI.

So where is the GUI saving the samba share information?

Thanks for your help in advance

---

### Post by dmizer on 2009-08-04
> **Blundey said:**
> So where is the GUI saving the samba share information?

The GUI doesn't save the share information anywhere.

Edit:
This is the line in smb.conf that deals with the shares you make in your GUI:
```
   usershare allow guests = yes
```

---

### Post by Blundey on 2009-08-04
huh? It must save some form of history to know which folders are enabled for sharing and which are not? If there was no config file then how does it know to reset file sharing on those folders and boot up?

Im confused.com

---

### Post by amac777 on 2009-08-04
The shares made from nautilus are stored here: 

/var/lib/samba/usershares

This page might help explain how nautilus-share works:

[http://gentoo.ovibes.net/nautilus-share/mediawiki-1.4.4/index.php/Accueil](http://gentoo.ovibes.net/nautilus-share/mediawiki-1.4.4/index.php/Accueil)

---

### Post by Blundey on 2009-08-04
Thank you! Exactly what I was looking for.

---

