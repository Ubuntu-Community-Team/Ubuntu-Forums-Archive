---
title: "Deja-dup restoring backup to another computer"
date: 2011-11-09
forum: General Help
---

### Post by obrer on 2011-11-09
Hello, 

Have made backup with password encryption of some directories of one of my computers, after have copied the resulting backup files to a different computer have tried to restore de data to an custom directory but does not recognise the password I encrypted the data. 

Is this normal, cannot restore backup data from into a different computer?

Thanks

---

### Post by notgary on 2011-11-10
I would expect Deja-Dup to have no problem doing this. A few things to try in order to diagnose the issue:

[LIST=1]
[*]Delete the current backup, reproduce it on the original computer and try to restore it on the destination to see if the problem is consistently reproducable. Are you able to do that a couple of times?
[*]Try mixing up the source and destination computers to see if the issue is with one of them.
[*]Try doing it without a password to see if it's just an issue with the encryption system or if that's just masking some deeper issue with the backup process.
[/LIST]
Let us know what the outcome of each of these tests is, and we can better diagnose your problem.

---

