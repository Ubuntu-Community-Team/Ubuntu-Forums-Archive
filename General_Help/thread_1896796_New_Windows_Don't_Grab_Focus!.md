---
title: "New Windows Don't Grab Focus!"
date: 2011-12-17
forum: General Help
---

### Post by ohnonot on 2011-12-17
I tried to find what is causing that behavior, using gconf-editor

/apps/metacity/general 

- but i can't see anything unusual there.
i've been playing around with it earlier but afaik everything's back to normal.
there's a screenshot of the keys.

i also checked gconf-settings for nautilus and made a search for "focus" but i can't find anything.

earlier i had replaced nautilus with thunar and then went back to nautilus again, i *think *that the problem started when going back to nautilus.

any help?

---

### Post by ohnonot on 2011-12-19
found the bugger.
it was a Screenlet called TextDateTime.
solved.

---

### Post by ohnonot on 2011-12-19
actually not.
it wasn't any particular screenlet, it was the option "always on top" that caused that behaviour.
actually the same with screenlets, which uses python scripts, and with desklets (which use some other language)
is it possible to have one always on top without interfering with the other windows' priorities?

---

