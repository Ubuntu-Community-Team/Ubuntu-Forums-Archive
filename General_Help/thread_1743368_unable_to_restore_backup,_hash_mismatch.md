---
title: "unable to restore backup, hash mismatch"
date: 2011-04-29
forum: General Help
---

### Post by u-noob-tu on 2011-04-29
i used deja dup to backup my home folder today so i could restore it after reinstalling 11.04. now, it starts to restore, but gives me this error every time: ```
Calculated hash: ac14ae0a7bf52c1ea0d851cec864df9e1c06b54e
Manifest hash: 4173054c0b0c8ce1154af5b5caae2a7591652765
```

i have no idea what that means, and im getting very annoyed.

---

### Post by u-noob-tu on 2011-04-29
*BUMP* any ideas?

---

### Post by Telengard C64 on 2011-04-29
Yeah. [By definition](http://www.answers.com/backup) the word *backup* means you end up with [more than one copy](http://www.dpbestflow.org/backup/backup-overview).

I don't use deja dup, but it looks to me something like this happned.

[list=1]
[*]You ran Deja dup to archive your files to the destination media
[*]Deja dup calculated a hash for the archived files
[*]You ran Deja dup to restore your files from the destination media
[*]Deja dup calculated a hash for the archived files
[*]The hashes don't match, which most likely means the archive is corrupt
[*]Deja dup refused to restore from a corrupt archive
[/list]

Like I said, not a deja dup user, so I'm only guessing here.

The whole point of a hash is to provide a means to verify that a set of data has not changed.

Maybe [this](http://live.gnome.org/DejaDup/Help/Restore/WorstCase#Restoring_by_Hand) will be helpful for you.

Good luck.

---

