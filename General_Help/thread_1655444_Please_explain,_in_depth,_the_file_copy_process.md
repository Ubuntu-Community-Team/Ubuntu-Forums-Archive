---
title: "Please explain, in depth, the file copy process"
date: 2010-12-29
forum: General Help
---

### Post by sofasurfer on 2010-12-29
I have a directory on my main drive. I have an older copy of it on my backup drive. I want to drag the directory, with all its files and folder, from the main drive over to the backup drive. When I do this I get this message, 

```
The source folder already exists in "pictures".  Merging will ask for confirmation before replacing any files in the folder that conflict with the files being copied
```

The buttons below this say cancel, skip all, merge all, skip, merge.
I do not understand what happens. I usually just press "merge all" and then "replace all" and everything goes as planned.

Do I have to replace everything or can I just, somehow, replace any file and folders that have changed?

I know about doing all of this with TAR but I am talking about drag n drop right now.

---

### Post by Norcalli on 2010-12-29
I don't think there is any way to replace updated files from the nautilus drag-and-drop, what you are describing is what "rsync"'s main function is, to copy over files only when they have been modified. It is mainly used as a backup utility. You can get more information from here:
[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

Also, for general backup advice:
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

