---
title: "Internal drive only automounts as read-only (Karmic Koala)"
date: 2010-01-06
forum: General Help
---

### Post by FatLabs on 2010-01-06
in case anyone else is having automount issues, this may help...

my internal storage drive was only mounting as read-only & Storage Device Manager would not permanently change it.  then i stumbled upon a fix by accident.

i have 2 other internal boot drives (1 with ubuntu 9,10 & 1 with win xp).  my storage drive would automount as read-only when the ubuntu drive was master & the win xp was slave.  but, when i switched it so that ubuntu drive is set to slave & the win xp drive is set to master, my 3rd storage drive automounted without the read-only preference.

i don't get it, but maybe it'll help someone else.

i stumbled on this fix while trying to solve another problem i'm having with my grub:
[**2nd hard drive won't boot (karmic koala)**]("http://ubuntuforums.org/showthread.php?t=1371700")

i'm still searching for an answer to the boot issue.

---

