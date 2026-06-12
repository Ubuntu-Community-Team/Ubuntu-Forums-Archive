---
title: "remove a locale"
date: 2011-03-24
forum: General Help
---

### Post by leniviy on 2011-03-24
Hi! I temporary added "ru_RU.UTF8 UTF8" to /var/lib/locales/supported.d/
and ran locale-gen.
Now 'locale -a' shows me the ru_RU.utf8 . 
I already removed this line from supported.d and even ran localepurge (it deleted plenty of files), rebooted, but 'locale -a' still shows ru_RU.utf8 .

---

### Post by Krytarik on 2011-03-24
Please see this thread: [http://ubuntuforums.org/showthread.php?t=1643502](http://ubuntuforums.org/showthread.php?t=1643502)

Hope it helps.

---

