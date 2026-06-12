---
title: "Lost top and side bars in nautilus (and other strange behavior)"
date: 2010-03-04
forum: General Help
---

### Post by marshmallow1304 on 2010-03-04
After starting up today, I noticed that nautilus has suddenly become quite minimalistic (see screenshot).  Additionally, each folder opens in a new window (didn't before) and turns gray when it is opened.  It looks the same running as root (except not themed, of course).

I've already done
```
sudo apt-get remove --purge nautilus
sudo apt-get install nautilus nautilus-share gnome-session
```


Also, gksu no longer works properly.  It always reports incorrect password, even when the password is correct.  Luckily, gksudo does work.  I don't know if this is related.

---

### Post by marshmallow1304 on 2010-03-04
Got it!

I'd never seen it before, but there's a setting in nautilus preferences (under the Display tab) labeled "Always open in browser windows".  I checked it and now all is well.

---

