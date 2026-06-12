---
title: "directory changed to file"
date: 2009-10-04
forum: General Help
---

### Post by Smintheu on 2009-10-04
Hi everybody,

I seemed to have accidentally changed a directory to a file with zero size. Any idea how i could change the file back to the directory?

Thanks!

---

### Post by drs305 on 2009-10-04
Did the directory/folder have contents? If not, simply delete the file and recreate the folder. In Nautilus, delete the file then File, Create Folder.

From the command line, if the folder and file belong to you:
```

rm /path/filename
mkdir /path/foldername

```

If the folder didn't belong to you, for instance a system folder belonging to root, tell us what the folder was.

---

### Post by Smintheu on 2009-10-04
the file used to be a directory containing some scripts of mine. It's probably also useful to mention that the file resides on a ntfs windows partition.. 

Thanks

---

