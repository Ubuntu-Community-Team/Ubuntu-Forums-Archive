---
title: "Is there a command to reload the desktop icons?"
date: 2010-02-14
forum: General Help
---

### Post by Rytron on 2010-02-14
Hello.
I notice that on rare occasions, all desktop icons disappear. Also I cannot change the wallpaper. I noticed this also in previous Ubuntu versions. If I go to Nautilus, I can view the Desktop items there. Is there a command to reload the desktop icons? Or is there another way besides resetting xorg/logging out?
Thanks.

---

### Post by rnerwein on 2010-02-14
hi
i think there is the desktop crashing. have you installed apport ( apt-get install apport ).
if there is a crash report in /var/crash it will be very usefull for the developer.
had the same problem only once during an update.
but sorry - how to restart it - i don't now but i think it's better to come up with a clean desktop after logout / login
ciao

---

### Post by OliW on 2010-02-14
This works for me sometimes: Press Alt+F2 and in that put:

```
nautilus -q && nautilus
```

That should kill off any stale nautilus sessions and boot a new one up for you.

---

### Post by Rytron on 2010-02-14
Thanks OliW. ;)

---

