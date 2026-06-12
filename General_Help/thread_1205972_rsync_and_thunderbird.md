---
title: "rsync and thunderbird"
date: 2009-07-06
forum: General Help
---

### Post by maclenin on 2009-07-06
Just wondering whether one can backup thunderbird (.mozilla-thunderbird) using rsync?

---

### Post by XCan on 2009-07-06
Sure, I don't see why not. Simply use 

rsync -avz /home/<usrname>/.mozilla-thunderbird /path/to/backup/

---

### Post by maclenin on 2009-07-07
Thanks, **XCan** - so rsync will keep tabs on incremental changes to thunderbird - i.e. new emails and other configuration changes?

I am experimenting with rsync/thunderbird now - and it seems to be doing just that - but I wanted to make certain before I "go live" with my backup plan....

Thanks for the comments.

---

### Post by XCan on 2009-07-07
You're welcome maclenin. Just a side notice, if you really want to keep track of all changes you might want to add the --delete flag as well as follows:

rsync -avz --delete /home/<usrname>/.mozilla-thunderbird /path/to/backup/

This will ensure that files that do not exist anymore in your home dir will be deleted from the backup as well.

rsync will keep track of the changes and modify the files as needed. :)

---

