---
title: "Any way to disable window border for google chrome(only)"
date: 2011-08-04
forum: General Help
---

### Post by DigitalAlcatraz on 2011-08-04
For some reason Google Chrome has two window borders, which irritates me(AS SHOWN IN ATTACHED IMAGE). Is there any way to disable window border just for Google Chrome?:popcorn:

---

### Post by SavageWolf on 2011-08-04
Spanner Menu Thing > Preferences > Personal Stuff > Use System title bars and borders?

---

### Post by CatKiller on 2011-08-04
I don't use Chrome, so SavageWolf's answer may well be exactly what you're after - making Chrome behave rather than you having to put up with its weirdness. If you like the weirdness and want Chrome to behave differently to everything else you can, as you requested, have that window specifically not decorated.

Install compizconfig-settings-manager and find the Window Decoration plugin settings. Change the setting for "Decoration windows" to exclude Chrome. It'll be something like ```
(any) & !(class=Chrome)
```

---

### Post by DigitalAlcatraz on 2011-08-04
Clicking it again does help but as soon as i maximize and un-maximize it the border reappears. Is there any way to change it using Compiz or something like that, not the browser?

---

### Post by CatKiller on 2011-08-04
> **DigitalAlcatraz said:**
> Is there any way to change it using Compiz or something like that, not the browser?

:confused:

You mean exactly like I've already told you how to do?

---

