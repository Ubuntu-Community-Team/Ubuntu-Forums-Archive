---
title: "Hamster time tracker global hotkey"
date: 2012-06-06
forum: General Help
---

### Post by taotree on 2012-06-06
I read on sites describing Hamster that there was a global hotkey to access it. It doesn't appear to work and I can't find anything in preferences about it. Is there some way to get it to work?

I'm using Ubuntu 12.04 LTS, 64-bit.

---

### Post by belda on 2013-02-25
If you are using compiz, you can use command plugin and to some hotkey assign this command, which will bring up dialog asking for current activity...
```
hamster-cli start "$(zenity --entry --text="Activity?")"
```

You need the zenity package installed.

---

