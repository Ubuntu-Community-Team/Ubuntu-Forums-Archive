---
title: "Where else are Software Sources listed?"
date: 2009-11-25
forum: General Help
---

### Post by sillyfofilly on 2009-11-25
Usually all of the software repositories I have added will show up in /etc/apt/sources.list but there are a few that show up in the Other Software tab in System->Administration->Software Sources that aren't in this file, in particular the google.com repository that was added when I installed Chrome, and the Docky repository that I added with
sudo add-apt-repository ppa:docky-core/ppa

Where are these listed?

---

### Post by drs305 on 2009-11-25
Take a look in /etc/apt/sources.list.d


*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

### Post by raktarok on 2009-11-25
Look here:

```
nautilus /etc/apt/sources.list.d/
```

---

### Post by sillyfofilly on 2009-11-25
Ok, I can see them all in there now.

Thank you.

---

