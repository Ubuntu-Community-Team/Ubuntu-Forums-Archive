---
title: "Firefox profile manager not working"
date: 2010-05-30
forum: General Help
---

### Post by arunsonnet on 2010-05-30
I've a problem with opening my firefox profile manager.
When I run ```
firefox
``` in the terminal, it works fine.
But when i run ```
firefox -p
```, it gives me the following error
```

run-mozilla.sh: Cannot execute /usr/lib/firefox-3.6.3/firefox-bin.pure.

```

---

### Post by lovinglinux on 2010-05-30
You need to use **-P** instead of **-p**.

---

### Post by arunsonnet on 2010-05-30
Thanks! I've been using the command in windows with "-p" and i got used to it. :D

---

### Post by lovinglinux on 2010-05-30
> **arunsonnet said:**
> Thanks! I've been using the command in windows with "-p" and i got used to it. :D

That's because Windows is not case-sensitive. See [http://ubuntuforums.org/showthread.php?t=1227827](http://ubuntuforums.org/showthread.php?t=1227827)

---

### Post by nomnex on 2010-05-30
you can call the Profile manager with the switch (case sensitive)

```
-P | -ProfileManager
```if you have more than one profile (default), you need the switch

```
-ProfileManager -no-remote
```If you want to launch your second profile (NNN) directly

```
firefox -P NNN -no-remote
```

---

