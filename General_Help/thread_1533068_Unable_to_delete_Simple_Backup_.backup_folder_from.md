---
title: "Unable to delete Simple Backup .backup folder from trash"
date: 2010-07-17
forum: General Help
---

### Post by SydneyGB on 2010-07-17
I'm a beginner at backing up my Ubuntu system, but I've set Simple Backup to do a backup once a week.  I deleted the oldest of these files, but now it's sitting in my Trash and I can't empty it. I get a permission denied error for the folders within the backup folder in the trash, yet I can't restore the folder either - Ubuntu says it 'failed to determine the original path' for the folder.  I've just discovered this in Xubuntu Jaunty, but I'm confident the same will happen in any other WM I choose (I have several installed - I like variety :) ).

It's not a huge file, but it's hanging out there and I'd like to get it either deleted or restored.  Possibly I oughtn't to have deleted it in the first place (it usually lives in /var/backup, which I can't access except as root).  The files, which I probably deleted /as/ root, show up in my user trash rather than root's trash.  I found the trash in ~/.local/share/Trash/files, but I'm not sure if just deleting them as root would be a good idea.

Any advice you good people can toss my way will be appreciated.  Thanks!

---

### Post by bobcollard on 2010-07-17
Start up your File Manager in Terminal.  Use the following code substituting the File manager's name for thunar if it is not that.  Then Empty the trash as root.
```
gksu thunar
```

---

