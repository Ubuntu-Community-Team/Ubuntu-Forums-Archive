---
title: "find and move files"
date: 2010-03-03
forum: General Help
---

### Post by howiebinnz on 2010-03-03
i have a large number of sub-folders (all in one "data" folder  - /home/howie/data/) with a variety of file types in them. i want to move all of one file type to a target folder. e.g. move all jpg file types to my "home/howie/Pictures" folder. I know i could do this "slowly" one folder at a time in nautilus with cut/paste, but there must be an easier way??? i can see find and move in the command line man but not sure how to combine them.
thanks for any pointers/help.

---

### Post by pholden on 2010-03-03
Something like the following should do the trick:

[user@machine ~]$ find data/ -type f -iname *.jpg -exec mv "{}" Pictures/ \;

:)

---

### Post by sisco311 on 2010-03-03
Something like:
```
find /home/howie/data -type f -iname "*.jpg" -exec **echo** mv -b -t /home/howie/Pictures '{}' +
```should do the trick.

Remove the **echo** command to actually move the files.

[uhelp]/community/find[/uhelp]

---

### Post by howiebinnz on 2010-03-03
that worked a treat, thanks for the quick response.:P

---

