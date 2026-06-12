---
title: "Spell Check Randomly Died in Pidgin..."
date: 2009-10-21
forum: General Help
---

### Post by beastrace91 on 2009-10-21
So I loaded up Pidgin today to discover that my spell checker was totally borked for some reason. All the words come up with red lines under them and there are no suggestions in the dictionary... Its like it is gone. 

I loaded Pidgin up via terminal and no error messages... Any suggestions on what might have changed and what I can do to correct the issue?

~Jeff

---

### Post by undecim on 2009-10-22
have you installed or uninstalled anything recently? If pidgin had already loaded before you messed with packages, it would still have that spell check library even if it got reinstalled for some reason.

Also, try closing pidgin, renaming the .purple directory in your home directory, and starting pidgin again. If that fixes it, it was a pidgin setting that caused it.

---

### Post by beastrace91 on 2009-10-22
Haven't added or removed anything recently. Removing the old .purple directory did not fix the issue so it is not a pidgin setting. 

I also tried removing and readding Pidgin to no avail.

~Jeff

---

