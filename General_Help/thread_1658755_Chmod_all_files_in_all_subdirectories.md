---
title: "Chmod all files in all subdirectories?"
date: 2011-01-03
forum: General Help
---

### Post by Argon on 2011-01-03
Hi!

I need to chmod all txt-files in a directory, including all files in all subdirectories, to 664. How to?

I've tried this with no result:

find . -type f -name "*\.txt" | xargs chmod 755

help anyone?

EDIT: changed from 775 to 664. Anyway, still doesn't work...

---

