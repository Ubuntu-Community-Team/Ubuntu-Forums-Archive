---
title: "set locale warning when running rsync"
date: 2011-07-09
forum: General Help
---

### Post by saintberry on 2011-07-09
Hi, 

Whenever I run rsync I get the following warning from setlocale:

```
bash: warning: setlocale: LC_ALL: cannot change locale (en_US.utf8)
```

This is on a basic install of Maverick Meerkat server with 2.6.38-7-generic kernel. In the past I have simply ignored the problem but since doing a lot of rsync and logging the result I'm finding this warning really annoying as it pollutes my logs.

When I run locale I get the following:

```
LANG=en_GB.UTF-8
LC_CTYPE="en_US.utf8"
LC_NUMERIC="en_US.utf8"
LC_TIME="en_US.utf8"
LC_COLLATE="en_US.utf8"
LC_MONETARY="en_US.utf8"
LC_MESSAGES="en_US.utf8"
LC_PAPER="en_US.utf8"
LC_NAME="en_US.utf8"
LC_ADDRESS="en_US.utf8"
LC_TELEPHONE="en_US.utf8"
LC_MEASUREMENT="en_US.utf8"
LC_IDENTIFICATION="en_US.utf8"
LC_ALL=en_US.utf8

```

And sudo dpkg-reconfigure locales

```
Generating locales...
  en_AG.UTF-8... up-to-date
  en_AU.UTF-8... up-to-date
  en_BW.UTF-8... up-to-date
  en_CA.UTF-8... up-to-date
  en_DK.UTF-8... up-to-date
  en_GB.UTF-8... up-to-date
  en_HK.UTF-8... up-to-date
  en_IE.UTF-8... up-to-date
  en_IN.UTF-8... up-to-date
  en_NG.UTF-8... up-to-date
  en_NZ.UTF-8... up-to-date
  en_PH.UTF-8... up-to-date
  en_SG.UTF-8... up-to-date
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... up-to-date
  en_ZW.UTF-8... up-to-date
Generation complete.
```

---

