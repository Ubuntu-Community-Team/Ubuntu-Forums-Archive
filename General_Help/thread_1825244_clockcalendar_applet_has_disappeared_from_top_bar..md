---
title: "clock/calendar applet has disappeared from top bar."
date: 2011-08-15
forum: General Help
---

### Post by switch10 on 2011-08-15
I just switched to 11.04 a few months ago, and I am still learning some of the new Unity stuff.  For the life of me, I cannot figure out how to get my clock back in the top bar (see screenshot).

Any help?

Thanks.

---

### Post by CatKiller on 2011-08-15
System -> Preferences -> Time & Date -> Clock -> Show a clock in the menu bar

---

### Post by switch10 on 2011-08-15
hmm.  I clicked on applications>system, and there is no preferences....

---

### Post by CatKiller on 2011-08-15
I don't use Unity, so I guess it could be somewhere else in there. You can run *indicator-datetime-preferences* and get the same preferences dialogue, anyway.

---

### Post by switch10 on 2011-08-15
I alt-f2ed indicator-daytime-preferences and nothing came up...

I recently uninstalled Evolution.  That must be the issue.  I forgot how integrated it was.  Its kind of ridiculous that I need a 20 mb plus package just to have a clock in my bar...

---

### Post by CatKiller on 2011-08-16
It's not daytime. It's **date**time.

You don't need Evolution to have the time displayed.

---

### Post by switch10 on 2011-08-16
> **CatKiller said:**
> It's not daytime. It's **date**time.

You don't need Evolution to have the time displayed.

ah yes, datetime.  Still nothing though...  Re-installing Evolution did not help either..

---

### Post by CatKiller on 2011-08-16
Re-installing Evolution wouldn't help; they are unrelated. It's possible that you uninstalled it during your random purge though. Running it in a terminal window might tell you which package provides it, or there's packages.ubuntu.com if it doesn't.

---

### Post by switch10 on 2011-08-16
Thanks!  indicator-datetime somehow was purged with Evolution.  Solved!

---

