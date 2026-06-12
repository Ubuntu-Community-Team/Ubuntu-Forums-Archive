---
title: "Prevent Skype Starting Automatically?"
date: 2011-12-17
forum: General Help
---

### Post by gus_zernial on 2011-12-17
I have Kubuntu 11.10 and installed Skype 2.2 Beta from the repositories. I use Skye infrequently and do not want it to start on boot - but not it for some reason starts three instances of Skype on booting.

I've searched for/through config files and I can't figure out what's starting it. How do I prevent Skype from starting on boot?

Thx, Gus

---

### Post by BC59 on 2011-12-17
For Kubuntu go to K menu--System Settings--Startup and Shutdown, Autostart. Or Alt-F2, type in start, Autostart. Uncheck Skype.

---

### Post by gus_zernial on 2011-12-17
That's what's confusing me. Skype is not there and thus
it's not checked.

---

### Post by BC59 on 2011-12-17
Then execute 

```
gksudo nautilus
```

and go to /etc/xdg/autostart and delete the entry of Skype.

---

