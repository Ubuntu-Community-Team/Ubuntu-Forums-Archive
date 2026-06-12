---
title: "How To - Easytag segfault fix"
date: 2006-03-24
forum: General Help
---

### Post by shof2k on 2006-03-24
Skill level - Beginner

Hi,
If you're experiencing a segfault when trying to use easytag, the following may help.

Open a terminal and type
```

cp ~/.easytag/easytagrc ~/.easytag/easytagrc_bkup
nano ~/.easytag/easytagrc

```

Delete any non character data and any lines with just an "=" sign present, then restart easytag.  This is a bug that should be fixed in the next version.

Many thanks to easytags main author, Jerome Couderc for putting up with my questions.

---

