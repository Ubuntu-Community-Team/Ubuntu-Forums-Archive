---
title: "Check with rsync if destination is up to date"
date: 2010-10-31
forum: General Help
---

### Post by skinns on 2010-10-31
I'm making a script to backup some stuff using crontab, is there anyway to tell if rsync actually needs to do something?

i.e.  if [everything in destination is not already up to date]; then do something
else do nothing

I've tried using the exit state ($?), but that gives '0' if something was updated or not.

Something involving rsync --dry-run maybe?

Thanks

---

### Post by J V on 2010-10-31
I would delve into the "--itemize-changes" option...

---

