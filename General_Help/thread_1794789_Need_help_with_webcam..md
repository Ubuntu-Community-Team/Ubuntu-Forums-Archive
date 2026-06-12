---
title: "Need help with webcam."
date: 2011-07-01
forum: General Help
---

### Post by TrickStyle on 2011-07-01
Hello,

I have a problem with my webcam. It works in Cheese! and gStreamer, but it isn't recognized on webcam-based websites like Chatroulette and Omegle, tinychat and/or similar.

Any further info about that please?

Thanks in advance.

---

### Post by no2498 on 2011-07-01
in/on fire fox look in tools abought plugins type in flash aid install it then run it
now go to the site you use right click click settings is that your cam
click a different folder that shows allow and remember
click them both
if you can not set it at the site go to the adobe site look for the settings manager 
you can set them at adobe if you went to the sites you use first

---

### Post by adit on 2011-07-01
Close all firefox windows.  Then start firefox by typing into terminal
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so firefox &
```

The above code was taken from post#3 in the thread:
[http://ubuntuforums.org/showthread.php?t=1148480](http://ubuntuforums.org/showthread.php?t=1148480)

---

### Post by TrickStyle on 2011-07-02
> **adit said:**
> Close all firefox windows.  Then start firefox by typing into terminal
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so firefox &
```

The above code was taken from post#3 in the thread:
[http://ubuntuforums.org/showthread.php?t=1148480](http://ubuntuforums.org/showthread.php?t=1148480)

```
ERROR: ld.so: object '/usr/lib/libv41/v411compat.so' from LD_PRELOAD cannot be preloaded: ignored.

```

---

### Post by TrickStyle on 2011-07-10
Bump

---

### Post by no2498 on 2011-07-10
you can set them at adobe if you went to the sites you use first
if you dont do as i said it never will work

---

