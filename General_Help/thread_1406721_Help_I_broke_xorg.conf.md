---
title: "Help I broke xorg.conf"
date: 2010-02-14
forum: General Help
---

### Post by odsus1 on 2010-02-14
8.04 studio

So I was minding my own business editing my xorg.conf and added a harmless little line under my "screen" section "virtual 1360 768" and all of a sudden ubuntu won't boot.  So I ran "sudo nano /etc/x11/xorg.conf" hoping to just remove the offending line, but when I opened it nano was blank. any help please?

Odie

---

### Post by Barriehie on 2010-02-14
**dexconf** will make a new one.

Barrie

---

### Post by odsus1 on 2010-02-14
Sweet! Thanks alot.

---

### Post by Barriehie on 2010-02-14
> **odsus1 said:**
> Sweet! Thanks alot.

No problem! 8)  Now when you get it fixed you can save a backup copy!

---

### Post by flippo on 2010-02-14
Just for completeness it appeared blank because its located at /etc/X11/xorg.conf (note the capital X in X11).  Unless you typo'd it when you posted.

---

### Post by fooman on 2010-02-14
> **odsus1 said:**
> 8.04 studio

So I was minding my own business editing my xorg.conf and added a harmless little line under my "screen" section "virtual 1360 768" and all of a sudden ubuntu won't boot.  So I ran "sudo nano /etc/x11/xorg.conf" hoping to just remove the offending line, but when I opened it nano was blank. any help please?

Odie

just so you know...the correct path is:

```
sudo nano /etc/[COLOR=Red]X[/COLOR]11/xorg.conf
```thats a upper case "X"...it was blank when you ran it because there is no /etc/x11/xorg.conf

oops...sorry, i am such a slooow typist.  someone always beats me to the punch.

---

### Post by odsus1 on 2010-02-14
> **flippo said:**
> Just for completeness it appeared blank because its located at /etc/X11/xorg.conf (note the capital X in X11).  Unless you typo'd it when you posted.

Syntax, it's a stinker, ain't it?

---

