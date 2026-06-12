---
title: "Finding Windows-illegal filenames"
date: 2011-06-18
forum: General Help
---

### Post by who-bear on 2011-06-18
I want to search a bunch of files in Ubuntu to find the ones that have file names which Windows won't allow. There is too many to do it manually. Any ideas?

---

### Post by inameiname on 2011-06-18
Try fslint.

sudo apt-get install fslint


It's handy for that sort of thing. Just be sure to run it as administrator to delete those things inside root folders.

---

