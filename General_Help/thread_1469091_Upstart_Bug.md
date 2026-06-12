---
title: "Upstart Bug?"
date: 2010-05-01
forum: General Help
---

### Post by emalamisura on 2010-05-01
Ok I am not sure if this a bug but it seems like it is...

If you create an upstart script in /etc/init without the .conf extension, it gets started at boot but you can't control it using initctl and it does not show up in initctl list, but its definitely running I have confirmed it.

This seems like a bug to me, either in Upstart boot up sequence of the initctl tool...

Am I mistaken?  I am using 10.04 btw...

---

