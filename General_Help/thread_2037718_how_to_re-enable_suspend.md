---
title: "how to re-enable suspend?"
date: 2012-08-05
forum: General Help
---

### Post by TheNessus on 2012-08-05
recently I have disabled suspend and enabled hibernation because the former worked less well than the latter.

But now i want to try suspend again, but I can't remember how I disabled it... :-\

help please?

12.04

---

### Post by Frogs Hair on 2012-08-05
Try system settings > Power or type Power into dash on Unity.

---

### Post by irv on 2012-08-05
If you are using a laptop just right click on the the battery in the top panel and select power settings.
[ATTACH]222296[/ATTACH]

---

### Post by TheNessus on 2012-08-05
no no it was something in

/etc/polkit-1/localauthority/50-local.d/com.ubuntu.disable-suspend.pkla

fixed it thanks!

---

### Post by irv on 2012-08-05
Please mark solved.

---

