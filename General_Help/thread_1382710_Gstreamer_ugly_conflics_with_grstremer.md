---
title: "Gstreamer ugly conflics with grstremer"
date: 2010-01-16
forum: General Help
---

### Post by elliotn on 2010-01-16
Is it safe for me remove my current gstreamer and install the bad ones, why u may ask, i want to play .dat video and it needs the gstreamer ugly set, it therefore conflics. Should I remove and install the one needed for da .dat video and will my mp3, mpg and avi files work with this set

---

### Post by mc4man on 2010-01-16
Unless you've installed some non standard gstreamer libs there should be no conflict between gstreamer plugins.

The only one I've seen is the gstreamer0.10-fluendo-mpegmux plugin (TS) conflicts with the gstreamer0.10-ugly, if that's the case it should be removed.

Otherwise what does this report (without following thru if wanting to remove package(s)

```
sudo apt-get install  gstreamer0.10-plugins-ugly
```

---

