---
title: "eMeSeNe not launching"
date: 2010-01-08
forum: General Help
---

### Post by Da CalebMan on 2010-01-08
Hey guys, I'm having problems with eMeSeNe (MSN messenger client),  I had changed something in the preferences menu, which caused the preferences window to stop opening. So thinking a 'reinstall' would fix it, I went into synaptic, and reinstalled it. I clicked on the menu, but it wouldn't launch at all, so I went to synaptic, and completely removed it, and the installed it again. Still nothing!

So then, I tried launching eMeSeNe from terminal, I got this:

```
'dude@hp-desktop:~$ emesene
If you are reading this, you may want to enable debug
It's the first option in the advanced page in preferences
Thread-1 start
/usr/share/emesene/FilterEntry.py:43: GtkWarning: Error parsing gtk-icon-sizes string:
	'panel-menu=24,24
panel=20,20
gtk-button=18,18
gtk-large-toolbar=24,24'
  self.entry.set_property('primary-icon-stock', gtk.STOCK_FIND)
sqlite3 imported
cabextract: No cabinet files specified.
Try 'cabextract --help' for more information.
'
```

No idea what that means! (Please keep in mind, I'm a newbie, so try not to get impatient with me
:))

Thanks! Please Reply!

---

### Post by akakingess on 2010-01-08
I am no expert by any stretch of the imagination, but I would first look in your home folder (where all of your Documents, Downloads, etc. are stored), and while looking in that folder hit CTRL+H, that's holding the Control key and hitting H, that will show your "hidden" folders, and find the one that corresponds to MSN (probably called ".msn") and notice the period before the name. Anyways, I would trash that folder altogether and then try a new fresh install.

EDIT:  Just keep in mind that the "hidden folders could be named anything, but should give you some sort of hint, like .microsoft or something...

---

### Post by Joeb454 on 2010-01-08
If you want to try the above, I believe (from memory, I haven't used emesene in a while) that the folder you'll want to move (you could just rename, rather than trash altogether) is going to be on of the following:
```
.emesene
.config/emesene
```

Either way, I'm sure you'll be able to find it :) Try that first, it sounds like it will solve the issue.

---

### Post by Da CalebMan on 2010-01-08
Thanks so much! It worked!:D

~Caleb

---

