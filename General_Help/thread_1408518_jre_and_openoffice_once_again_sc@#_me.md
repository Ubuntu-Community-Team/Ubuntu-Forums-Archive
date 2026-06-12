---
title: "jre and openoffice once again sc@# me"
date: 2010-02-16
forum: General Help
---

### Post by Mark_in_Hollywood on 2010-02-16
I tried to load the Letter from the openoffice "wizard". It said I needed Java Runtime Environment. I installed jre -no problem. 

Went back to openoffice, opitons, java, tried to add it, must have missed where the executable was. Now I cannot uninstall the damn thing. 

blewey!

Why is this such an on-going hassle?

Why doesn't someone at Ubuntu write a script or an easy how to?

---

### Post by Hagar Delest on 2010-02-16
Never had any issue with JRE.

Try to [reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403) but don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile.

If no change, try the Sun version perhaps: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by Mark_in_Hollywood on 2010-02-16
Thanks for that, yet, please don't take umbrage when I say that NONE of that should be necessary. _JRE sucks_. It should be easy, it should need fixing.

Even after finding ~/user and renaming it user.old, restarting OOo, and going to Tools/// and java, it's still installed and NOT working.

Meanwhile, while your posts are (maybe the only) help, it's just too complicated to take the time to fix it.


The OpenOffice.org team need to make jre "Un-installable", just in case of problems.

Thanks again.

---

### Post by NovaAesa on 2010-02-16
> **Mark_in_Hollywood said:**
> _JRE sucks_I hardly see how it's JRE's fault. Isn't it a problem with OO?

---

### Post by Hagar Delest on 2010-02-17
Try that one perhaps: [[Solved] Some wizards receive defective JRE error]("http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=5463").

---

### Post by FuturePilot on 2010-02-17
How did you install Java?

---

### Post by cariboo on 2010-02-17
Moved to General Help, this is a support question, not a Cafe thread.

---

### Post by Hagar Delest on 2010-02-17
Personally, I install from the Sun site with their auto-installer file. But in previous version I've also used the version delivered out of the box with Ubuntu.

---

### Post by Mark_in_Hollywood on 2010-02-21
Hagar de l'Est. Thanks. Following the thread at

[[Solved] Some wizards receive defective JRE error]("http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=5463")

and using Syn pkg mgr, I instaled:

openoffice.org-java-common

and

openoffice.org-gcj

returning to OpenOffice Writer, the Wizard works.

For the record, here:

This is a clean install of Karmic Koala v. 9.10. It is about a two month old install. This is a stock install, nothing modified. OpenOffice is found under Applications/Office. No mods have been made to OpenOffice during this time. Whatever wasn't on the karmic .iso, is sure a pain in the butt. And unless you are counselled by:

**Hagar de l'Est**

you don't know diddly

Merci!

---

