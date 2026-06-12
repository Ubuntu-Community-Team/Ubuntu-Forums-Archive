---
title: "Can't reach Administrator Mode"
date: 2006-02-27
forum: General Help
---

### Post by Qwertie on 2006-02-27
System Settings ignores requests to enter Administrator Mode ... it gives no error message, whether the password I input is correct or incorrect.

I can still use sudo and su, so what's wrong?

By the way, it used to work.  I don't know what changed.

---

### Post by incubus on 2006-02-27
Are you getting that using your regular user, not root?

---

### Post by Qwertie on 2006-02-27
Yes.

---

### Post by aysiu on 2006-02-27
Try Alt-F2 ```
kdesu systemsettings
```

or

Alt-F2 ```
kdesu kcontrol
```

---

### Post by Qwertie on 2006-02-28
Thanks, that works!  Now how can I fix it so it works how it is supposed to?

Also, why the heck are there two KDE control panels?

---

### Post by FlakJacket on 2006-02-28
The beauty of Open Source.  You could make your own control panel if you wanted.  System Settings I believe is a Kubuntu project while KControl is a KDE standard control panel.  They both use the same modules I believe but just arrange them differently. 

Hope that answers your second question,
 Flak

BTW I'm not sure if this problem has been fixed in KDE 3.5.1 .  Anyone know?

---

### Post by Jucato on 2006-02-28
The Administrator Mode is, I think, a bug in KDE 3.4.x. 
I think it was fixed in KDE 3.5.1

OT: I just dislike the 2 Kubuntu projects (Adept and System Settings). Maybe I just expected too much from them. :D

---

### Post by gingermark on 2006-02-28
[QUOTE=FlakJacket]The beauty of Open Source.  You could make your own control panel if you wanted.  System Settings I believe is a Kubuntu project while KControl is a KDE standard control panel.  They both use the same modules I believe but just arrange them differently. 

Hope that answers your second question,
 Flak

BTW I'm not sure if this problem has been fixed in KDE 3.5.1 .  Anyone know?[/QUOTE]
It has been fixed in 3.5.1
And System Settings seems to not contain all the KControl modules unfortunately.

---

