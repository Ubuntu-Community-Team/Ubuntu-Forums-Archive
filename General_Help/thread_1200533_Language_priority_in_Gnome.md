---
title: "Language priority in Gnome"
date: 2009-06-30
forum: General Help
---

### Post by coudy on 2009-06-30
Hi, 
I have problem with language priority in Gnome. Some programs which are not translated to Slovak language, but they are translated to Czech language still start in English.

output from /etc/default/locale
```
LANGUAGE="sk_SK:sk:cs_CZ:cz:en_GB:en"
LANG="sk_SK.UTF-8

```locale output from gnome-terminal
```

LANG=sk_SK.UTF-8
LC_CTYPE="sk_SK.UTF-8"
LC_NUMERIC="sk_SK.UTF-8"
LC_TIME="sk_SK.UTF-8"
LC_COLLATE="sk_SK.UTF-8"
LC_MONETARY="sk_SK.UTF-8"
LC_MESSAGES="sk_SK.UTF-8"
LC_PAPER="sk_SK.UTF-8"
LC_NAME="sk_SK.UTF-8"
LC_ADDRESS="sk_SK.UTF-8"
LC_TELEPHONE="sk_SK.UTF-8"
LC_MEASUREMENT="sk_SK.UTF-8"
LC_IDENTIFICATION="sk_SK.UTF-8"
LC_ALL=

```locale output from CTRL+F1 (tty)
```

LANG=sk_SK.UTF-8
**LANGUAGE=sk_SK:sk:cs_CZ:cz:en_GB:en**
LC_CTYPE="sk_SK.UTF-8"
LC_NUMERIC="sk_SK.UTF-8"
LC_TIME="sk_SK.UTF-8"
LC_COLLATE="sk_SK.UTF-8"
LC_MONETARY="sk_SK.UTF-8"
LC_MESSAGES="sk_SK.UTF-8"
LC_PAPER="sk_SK.UTF-8"
LC_NAME="sk_SK.UTF-8"
LC_ADDRESS="sk_SK.UTF-8"
LC_TELEPHONE="sk_SK.UTF-8"
LC_MEASUREMENT="sk_SK.UTF-8"
LC_IDENTIFICATION="sk_SK.UTF-8"
LC_ALL=

```

My system>
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04"
Linux coudy 2.6.28-13-generic #44-Ubuntu SMP Tue Jun 2 07:57:31 UTC 2009 i686 GNU/Linux

How to solve this problem ? Thank You

---

### Post by coudy on 2009-07-01
any idea ?

---

### Post by coudy on 2009-07-06
obviously is this bug, so I decided to create bug report.
If someone has same problem, report it here
[https://bugs.launchpad.net/ubuntu/+bug/396003](https://bugs.launchpad.net/ubuntu/+bug/396003)

---

