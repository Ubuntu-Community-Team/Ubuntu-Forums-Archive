---
title: "Language setting problem"
date: 2011-04-20
forum: General Help
---

### Post by freexlander on 2011-04-20
hi all im a novice user of ubuntu! i have problem with language settings. most of the components and menus are in chines language. i tried to change the language from language menu but that was totally in chines... is there a terminal command to change language to English?

thanx in advance!

for more illustrations please take a look at attached screen shot

---

### Post by zvacet on 2011-04-21
See if [this]("http://ubuntuforums.org/showthread.php?t=1632229") helps.

---

### Post by btindie on 2011-04-21
You can change the default language by editing /etc/default/locale. From a terminal type
```
$ sudoedit /etc/default/locale
```Mine contains
> LANG="en_GB.UTF-8"
Reboot and it should then use that for your account provided it hasn't been overridden locally.

---

### Post by dino99 on 2011-04-21
sudo dpkg-reconfigure locales

---

