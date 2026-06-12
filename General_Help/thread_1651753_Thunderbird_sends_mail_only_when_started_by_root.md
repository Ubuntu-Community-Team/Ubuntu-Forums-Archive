---
title: "Thunderbird sends mail only when started by root"
date: 2010-12-23
forum: General Help
---

### Post by Artur D on 2010-12-23
Hi, I have 2 email accounts set up in Thunderbird - one is gmail and the other was given me by our server admins few years ago. Everything works fine on windows but when I try to send something from the second account (not gmail) in ubuntu it says that password is incorrect. Ive double checked all settings and seems like everything set correct. Now the most interesting part: when I set up this account as root (gksu thunderbird and then do same as I did under my account) everything works perfect. 

I found only one thread at this forum with same issue and sure it's not solved :( [http://ubuntuforums.org/showthread.php?t=1424977](http://ubuntuforums.org/showthread.php?t=1424977) (BTW, I don't have /opt/thunderbird directory)

---

### Post by sefs on 2010-12-23
> **Artur D said:**
> Hi, I have 2 email accounts set up in Thunderbird - one is gmail and the other was given me by our server admins few years ago. Everything works fine on windows but when I try to send something from the second account (not gmail) in ubuntu it says that password is incorrect. Ive double checked all settings and seems like everything set correct. Now the most interesting part: when I set up this account as root (gksu thunderbird and then do same as I did under my account) everything works perfect. 

I found only one thread at this forum with same issue and sure it's not solved :( [http://ubuntuforums.org/showthread.php?t=1424977](http://ubuntuforums.org/showthread.php?t=1424977) (BTW, I don't have /opt/thunderbird directory)


If that were me I would not run thunderbird with gsku.  I would just run it as the logged in user, and set up the account which would create a TB profile in the logged in users home directory.

---

### Post by Artur D on 2010-12-23
Well, that's an easy way :) But I really want to fix this

---

### Post by Verbeck on 2010-12-23
try removing the old config files
from a terminal,
```

mv ~/.thunderbird ~/.thunderbird.backup

```

---

### Post by Artur D on 2010-12-23
I've already tried this (btw it was first clean installation)

---

### Post by Artur D on 2010-12-24
anyone?

---

### Post by Artur D on 2010-12-25
I really need to fix this guys :(

---

### Post by WorMzy on 2010-12-25
There is no difference between how the application runs under gksu and how it runs under your user. The only difference is the configuration it uses: gksu uses root's config, and normal uses your config. If it works with gksu, then there is something wrong with *your* config. All I can suggest is that you double-check *your* settings.

If you really can't see what's going wrong, then copy root's settings into your home area:
```
mv ~/.thunderbird ~/.thunderbird.old
```
```
sudo cp /root/.thunderbird /home/***username*/**
```
```
sudo chown -R ~/.thunderbird
```

Note that I'm assuming that Thunderbird stores it's data in ~/.thunderbird. It may be in ~/.local/thunderbird, or ~/.mozilla/thunderbird. Also, replace "***username***" with your username.

---

