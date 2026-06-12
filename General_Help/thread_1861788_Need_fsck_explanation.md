---
title: "Need fsck explanation"
date: 2011-10-16
forum: General Help
---

### Post by afajknaz on 2011-10-16
11.10 update broke my OS, so I took an old hard drive, copied my home directory to it and reinstalled. After I got a fresh OS, I wanted to restore the copy and - surprise - the backup is broken, fsck complains about bad magic number. I found a guide that advised to use one of backup magic numbers. After I did so, I received a ton of messages like:
```
Directories count wrong for group #56 (0, counted=2)
```Now, the message suggests that my disk has stored a number 0 and fsck wants to replace it with 2. But it's not super clear about it and having a ton of errors where it could replace a correct number with 0 makes me want to play it safe. So which number is which?

---

