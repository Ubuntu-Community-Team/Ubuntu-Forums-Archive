---
title: "Booting in gui issue"
date: 2009-11-13
forum: General Help
---

### Post by mrmagoo1077 on 2009-11-13
When i restart/power up my computer the screen goes dark.  If i press Control alt Delete it brings me to a menu where i can select ubuntu recovery mode.  Ubuntu than starts up in the comman line version (no gui, still havent learned the lingo).  the startx command fails giving me an error about my user account, than freezes.  If instead i type "sudo startx" it than boots up nearly normal (wine doesnt work for some reason?).  I am now logged in as ROOT instead of my user account.  Which doesnt make sense to me because everything thing ive read stated ROOT is disabled in ubuntu.  Ubuntu Version 9.10 with recent updates (did it before updates too)

---

### Post by Giblet5 on 2009-11-13
Boot into recovery mode shell.

Enter ```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
exit
```

Continue the normal boot.

Better?

---

### Post by mrmagoo1077 on 2009-11-14
i get "mv: cannot stat '/etc/X11/xorg.conf' no such file or directory"

---

