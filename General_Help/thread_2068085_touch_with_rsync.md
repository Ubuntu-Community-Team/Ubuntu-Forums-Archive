---
title: "touch with rsync"
date: 2012-10-08
forum: General Help
---

### Post by Drenriza on 2012-10-08
Hey guys.

I have a rsync command as follows in a expect script
```
spawn rsync -a -r -z -v -h -p -i --log-file=/path/rsync.log --progress --delete-excluded -e ssh user@ip:/source /destination
```

My question is.
When rsync has downloaded a file or folder, how can i get rsync to touch the file / folder with a date and timestamp for when the download was completed on the destination?

Thanks on advance.
Kind regards.

EDIT.
So i see that -a preserves for example timestamps.

EDIT2.
Changed -a out with -o and -g along with -p these preserve the group, owner and permissions but not symbolic links and timestamps.
Problem solved.

---

