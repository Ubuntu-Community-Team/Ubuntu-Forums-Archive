---
title: "No command arguments supplied! No command arguments supplied! Usage: kdesudo"
date: 2010-03-10
forum: General Help
---

### Post by noveevon on 2010-03-10
No command arguments supplied!
Usage: kdesudo [-u <runas>] <command>
KdeSudo will now exit...

is a error message i get every time i log in, ive just installed a fresh 9.10...and ive got the latest updates..

any solutions?

---

### Post by noveevon on 2010-03-10
its not come back now, after i switched some multiple screen settings...

---

### Post by jerryablan on 2010-05-03
Howdy folks, I got this today too and figured out how to fix it.

If you look in your ~/.kde/share/config directory there is a file called ksmserverrc. 

Edit that file and remove all the config items in LegacySession and Session. 

I think it's a bug in ksmserver incorrectly recording bogus session items.

Hope that helps! 

-- Jerry

---

