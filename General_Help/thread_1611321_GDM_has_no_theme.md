---
title: "GDM has no theme"
date: 2010-11-01
forum: General Help
---

### Post by josephellengar on 2010-11-01
Can't quite figure this out.  My GDM is showing up with no theme whatsoever.  It has a completely black background, boxy buttons, and ugly fonts.  I can change it by going to tty1 and using

```

sudo -u gdm gnome-control-center

```

But when I restart it is back to the same.  Any ideas?

---

### Post by josephellengar on 2010-11-03
bump

---

### Post by sikander3786 on 2010-11-03
Did you try purging and reinstalling gdm?

```
sudo apt-get remove --purge gdm
```

```
sudo apt-get install gdm
```

---

### Post by zaenal on 2011-05-27
I had similar problem.
Problem solved after purging and reinstalling gdm.

Thanks.

---

