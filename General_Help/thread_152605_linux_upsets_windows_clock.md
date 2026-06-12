---
title: "linux upsets windows clock"
date: 2006-03-30
forum: General Help
---

### Post by frizzl on 2006-03-30
hi guys...

after using ubuntu, then rebooting back into windows, my windows clock will be set forward 2 hours. The ubuntu clock is correct however.

What could be the problem?

---

### Post by Marshall2day on 2006-03-30
Perhaps the installation set your bios time on local in stead of GMT? I remember the installer asks something like that. In which timezone do you live?

---

### Post by frizzl on 2006-03-30
i live in GMT + 10 (which i set in the installer...) which is Australia.

the time in linux is correct, but windows and bios are 2 hours ahead :S

---

### Post by DexterBelgium on 2006-03-30
Ubuntu sets the system clock to GMT, no matter what time zone you live in. It then, depending on the timezone, adds or subtracts. This is the way people agreed computers SHOULD work (it's some kind of standard).

However, windows does not follow this standard. There is, however, a way to get ubuntu to set the system clock to local time and not GMT. Don't know how, but if you search, you should find it.

---

### Post by ronmarley1 on 2006-03-30
Hi frizzl,
Go to a terminal and type ```
sudo gedit /etc/default/rcS
``` Change UTC=yes to UTC=no.  Then save and exit.

---

### Post by frizzl on 2006-03-30
thankyou greatly ronmarley1 :D

that worked perfectly. I really am beginning to like ubuntu!

---

### Post by ronmarley1 on 2006-03-30
[QUOTE=frizzl]thankyou greatly ronmarley1 :D

that worked perfectly. I really am beginning to like ubuntu![/QUOTE]

Glad I could help.  Ubuntu is really the best Linux community, hands down!

---

