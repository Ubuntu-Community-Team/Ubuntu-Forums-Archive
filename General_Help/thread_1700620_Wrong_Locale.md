---
title: "Wrong Locale"
date: 2011-03-05
forum: General Help
---

### Post by zebala on 2011-03-05
I recently installed language packs for Japanese and changed my system language to it, too. The problem is, now that I try to go back to English, the locale doesn't change back, only the menus are in english. "Apply system wide" in the Language Support didn't do anything; Firefox is in japanese too. Here is my locale output:

LANG=ja_JP.utf8
LANGUAGE=en_US:en
LC_CTYPE="ja_JP.utf8"
LC_NUMERIC="ja_JP.utf8"
LC_TIME="ja_JP.utf8"
LC_COLLATE="ja_JP.utf8"
LC_MONETARY="ja_JP.utf8"
LC_MESSAGES="ja_JP.utf8"
LC_PAPER="ja_JP.utf8"
LC_NAME="ja_JP.utf8"
LC_ADDRESS="ja_JP.utf8"
LC_TELEPHONE="ja_JP.utf8"
LC_MEASUREMENT="ja_JP.utf8"
LC_IDENTIFICATION="ja_JP.utf8"
LC_ALL=

/var/lib/locales/supported.d/local
:
en_US.UTF-8 UTF-8

/etc/default/locale
:
LANG="en_US.utf8"
LANGUAGE="en_US:en"

I'm confused since everything should be set right. I tried "sudo dpkg-reconfigure" but it didn't do the trick. Any help is greatly appreciated.. Thank you.

---

### Post by zebala on 2011-03-06
Bump. I could really use some help guys!

---

