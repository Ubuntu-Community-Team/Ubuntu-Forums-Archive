---
title: "Pidgin crashing in Karmic"
date: 2009-11-03
forum: General Help
---

### Post by Famicommander on 2009-11-03
I did a fresh install of Ubuntu Karmic yesterday and the only hitch so far is that Pidgin keeps crashing on me. It only happens every once in awhile, but it's annoying nonetheless.

It's a basic Pidgin install on 32-bit Karmic with gfire and facebook-chat plugins.

Naturally, I ran the program via terminal to diagnose the problem and this is what I came up with:
```
jason@ubuntu:~$ pidgin

(pidgin:22690): GStreamer-CRITICAL **: gst_object_unref: assertion `((GObject *) object)->ref_count > 0' failed

(pidgin:22690): GStreamer-CRITICAL **: gst_object_unref: assertion `((GObject *) object)->ref_count > 0' failed

(pidgin:22690): GStreamer-CRITICAL **: gst_object_unref: assertion `((GObject *) object)->ref_count > 0' failed
Segmentation fault

```

Anyone have any idea how to fix that?

---

### Post by Famicommander on 2009-11-05
Still having this issue...

---

### Post by Famicommander on 2009-11-05
Day three and counting...

---

### Post by Famicommander on 2009-11-07
Day four...

---

### Post by Famicommander on 2009-11-08
I suppose nobody cares?

---

### Post by ElSlunko on 2009-11-08
I don't use gfire but have you tried removing 1 addon and then the other to perhaps single out which is causing the crash?

---

### Post by nathanernest on 2009-11-08
There have been a few posts about im clients crashing in the last few days. The bigest fix seems to be download the updated version of facebook chat (fixed all problems for me). Another suggestion would be to use empathy instead of pidgin... :-)

---

### Post by Famicommander on 2009-11-08
Still crashing after updating to the newest facebook-chat.

---

