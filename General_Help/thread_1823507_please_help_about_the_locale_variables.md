---
title: "please help about the locale variables"
date: 2011-08-12
forum: General Help
---

### Post by wxuyec on 2011-08-12
hi, everyone
when I use locale command, I got
~$ locale
LANG=zh_CN.UTF-8
LANGUAGE=zh_CN:en
LC_CTYPE="zh_CN.UTF-8"
LC_NUMERIC="zh_CN.UTF-8"
LC_TIME="zh_CN.UTF-8"
LC_COLLATE="zh_CN.UTF-8"
LC_MONETARY="zh_CN.UTF-8"
LC_MESSAGES="zh_CN.UTF-8"
LC_PAPER="zh_CN.UTF-8"
LC_NAME="zh_CN.UTF-8"
LC_ADDRESS="zh_CN.UTF-8"
LC_TELEPHONE="zh_CN.UTF-8"
LC_MEASUREMENT="zh_CN.UTF-8"
LC_IDENTIFICATION="zh_CN.UTF-8"
LC_ALL=
but when I 
~$echo $LC_CTYPE
I got a blank result.
what happened?
thank you

---

### Post by jake.anq on 2011-08-12
Hi

Try using
```
printenv LC_CTYPE
```
to print environment variables

---

