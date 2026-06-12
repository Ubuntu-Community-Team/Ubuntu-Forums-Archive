---
title: "how to clean Empathy's config?"
date: 2010-05-05
forum: General Help
---

### Post by dbloom on 2010-05-05
hi,

i've never been able to use empathy.  for some reason, i just can't add accounts.  i've messed with it a lot in karmic, but gave up.  running lucid now and added a profile for my wife.  interestingly, she has no problems using empathy so i think there must be something going on with my settings.

i've searched and searched and removed everything i could find that was empathy-related, but no luck. 

does anyone have any advice on this? thanks!

---

### Post by matrixblue on 2010-07-23
In terminal run: **sudo apt-get purge empathy** then **sudo apt-get install empathy** and try again

---

### Post by darolu on 2010-07-23
Empathy files are stored in:
```
~/.gconf/apps/empathy
```

Maybe you can manually fix it there, deleting the xml files may work (fresh start).

Added: the actual accounts information is stored at:
```
~/.mission-control/accounts/
```

---

### Post by dbloom on 2010-07-26
thanks, darolu!  removing the accounts under .mission-control/ let me add my accounts correctly.  finally!

---

