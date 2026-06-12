---
title: "Removing duplicate (old) files upon sbackup restore"
date: 2011-02-23
forum: General Help
---

### Post by kcxzero on 2011-02-23
Hey, I was wondering if there was a way to instruct sbackup to remove the old files or replace them with the backed up files when doing a restore. Otherwise, after doing a restore won't there be two copies of everything?

Thanks.

---

### Post by yoramdavid on 2011-12-17
I had the same problem and did not find an easy solution.
What I did was a search for the file names with "_before_restore" and deleted all the files like this. It was a long process!

A better solution would be nicer.

Yoram

---

### Post by yoramdavid on 2011-12-24
And to my surprise, when I crated an new user, it created the user with also file named ***before_restore*** !??

---

