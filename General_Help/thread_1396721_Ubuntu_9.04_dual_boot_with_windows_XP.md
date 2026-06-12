---
title: "Ubuntu 9.04 dual boot with windows XP"
date: 2010-02-02
forum: General Help
---

### Post by karthick87 on 2010-02-02
I have installed ubuntu 9.04 and windows XP in my system..Is it possible to lock Windows xp in the grub menu so that logging on to windows XP is denied..

---

### Post by karthick87 on 2010-02-06
Bump...

---

### Post by warfacegod on 2010-02-06
Any particular reason why?

---

### Post by karthick87 on 2010-02-06
I dont like to remove XP and also other users  used to use XP and download large files where as in ubuntu i have installed Squid and download was restricted...That why i want to lock Windows entry from grub so that the user cant able to use XP...

---

### Post by warfacegod on 2010-02-06
If you want to completely lock down XP, that would make it useless, so why not remove it?

---

### Post by Leppie on 2010-02-06
why don't you set the timeout to something like 1 second and hide the boot menu?

---

### Post by karthick87 on 2010-02-06
I would like to use XP later,so can you tell me the way to lock it..

---

### Post by warfacegod on 2010-02-06
I imagine removing it from GRUB would suffice.

[http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2]("http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2")

---

### Post by karthick87 on 2010-02-06
SO if i remove the XP entry from Grub,can i able to use ubuntu?

---

### Post by warfacegod on 2010-02-06
> **getyourkarthick said:**
> SO if i remove the XP entry from Grub,can i able to use ubuntu?

Yes.

---

### Post by Leppie on 2010-02-06
removing other os entries from your boot menu, doesn't affect your ubuntu installation.

---

### Post by Leppie on 2010-02-06
> **warfacegod said:**
> I imagine removing it from GRUB would suffice.

[http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2](http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2)
this link is for grub2, juanty still uses grub legacy.

you can use startup manager for this, System>Administration>Startup Manager. i think it is already installed in a standard ubuntu install, otherwise install like this:
```
sudo apt-get install startupmanager
```

---

