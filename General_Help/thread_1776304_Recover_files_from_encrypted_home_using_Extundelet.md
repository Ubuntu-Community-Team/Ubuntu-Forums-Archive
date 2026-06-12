---
title: "Recover files from encrypted home using Extundelete?"
date: 2011-06-05
forum: General Help
---

### Post by kjkoec on 2011-06-05
I've been using Extundelete 2.0 to "undelete" files off of my main ubuntu partition.  
Now, however, I am trying to perform this operation on my main, **encrypted**, home dir.
I am not entirely certain if I need to decrypt if, but if I do, how can I?

The command:
```
ecryptfs-mount-private
```
merely unlocks the folder while it's partition is ***mounted***, correct?

Extundelete requires part's to be ***unmounted*** so as to not overwrite data... but should it even need to unlock my home dir if it only checks the journal and restores inodes, as it then moves the data to a new folder in your current working dir?

My situation is not life or death, as the mentioned files are not of the utmost importance to be restored, but I would nevertheless like to recover them, if possible.
If anyone can offer an answer to any of my questions, it would be well-appreciated.

---

