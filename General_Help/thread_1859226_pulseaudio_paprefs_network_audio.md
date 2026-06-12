---
title: "pulseaudio paprefs network audio"
date: 2011-10-13
forum: General Help
---

### Post by oly on 2011-10-13
just found out paprefs is broken in oneric it trys to load modules in a path that does not exist you can fix it with the below command.

sudo ln -s /usr/lib/pulse-1.0 /usr/lib/pulse-1.0.0

you can use strace paprefs to find the path its looking if you ever need to.

you can then enable streaming audio and dlna options in pulseaudio by running paprefs.

---

### Post by mapuo on 2011-10-26
Thank you! :)

---

