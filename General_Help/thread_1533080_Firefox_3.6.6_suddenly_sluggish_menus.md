---
title: "Firefox 3.6.6 suddenly sluggish menus"
date: 2010-07-17
forum: General Help
---

### Post by dschaller on 2010-07-17
Using Firefox 3.6.6 on Ubuntu 8.04. Everything working fine until a day or two ago. I installed the LastPass add-on and noticed that all of a sudden the drop-down menus took about 5 seconds each to open. Changing search engines, opening bookmark folders, opening file/edit/view, etc. was all very slow to respond.

I thought LastPass might be the culprit, so I uninstalled it. It didn't help. Then I tried starting Firefox in safe mode. Still the same issue. So maybe LastPass wasn't really the trouble.

Has anyone else run into this? Any ideas?

---

### Post by lovinglinux on 2010-07-17
Create a new profile and check if it is sluggish too.

Start Firefox with:

```
firefox -P
```

If the new profile works better, then see [Fixing a problematic or corrupted profile](http://firefox-tutorials.blogspot.com/2010/05/fixing-problematic-or-corrupted-profile.html).

---

