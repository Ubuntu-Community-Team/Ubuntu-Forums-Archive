---
title: "openoffice word processor graphics is smeared"
date: 2011-08-11
forum: General Help
---

### Post by chenyo on 2011-08-11
hi guys,
ive installed linux ubunto 10.04 a week a go ,works great.
when i first open my OpenOffice word and typing some things ive notice a smearing
effect on the menus.

why is this happaning?
is this my graphic card?maybe accelaration stuff?

please help me :)

---

### Post by Hagar Delest on 2011-08-11
Is it the same if you change the theme of your desktop?

Else, try to install the vanilla version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by LowSky on 2011-08-11
that isn't a graphics issue I have seen. especially if it is screwing up only openoffice.

you are not the only person to have seen this problem
[http://ubuntuforums.org/showthread.php?t=1602603](http://ubuntuforums.org/showthread.php?t=1602603)

try updating to the newest version
```

sudo add-apt-repository ppa:openoffice-pkgs/ppa

sudo apt-get update && sudo apt-get upgrade

sudo apt-get install openoffice.org-gnome
```

---

