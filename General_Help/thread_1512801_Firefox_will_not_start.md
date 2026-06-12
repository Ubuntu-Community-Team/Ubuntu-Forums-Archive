---
title: "Firefox will not start"
date: 2010-06-18
forum: General Help
---

### Post by llong0415 on 2010-06-18
Thanks for the post, but I installed NoScript and now Firefox wont start. I've apt-get remove --purge 'd, then re-installed. Still wont work. Tried to delete the folders and no luck there either. Any help would be greatly appreciated. I'm running 10.04 and everything is up to date.

---

### Post by bodhi.zazen on 2010-06-18
Moved to general help.

Hard to know how noscript would be causing this problem.

Can you try starting firefox in a terminal and posting any error messages.

Open a terminal

```
firefox
```

---

### Post by WorMzy on 2010-06-18
Try opening firefox in safemode (alt+F2, "firefox --safe-mode", run). if that starts up then you can remove noscript from the list of extenstions, then restart firefox.

Failing that, you should be able to "uninstall" noscript by deleting the following folder: ~/.mozilla/firefox/profiles/<profilename>/extensions/{73a6fe31-595d-460b-a920-fcc0f8843232}

If someone could confirm that, I'm not sure if the ID differs from PC to PC.

Last resort: create a new profile by running "firefox -P".

---

