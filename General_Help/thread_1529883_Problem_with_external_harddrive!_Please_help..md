---
title: "Problem with external harddrive! Please help."
date: 2010-07-12
forum: General Help
---

### Post by petewheat on 2010-07-12
Okay, so I have an external harddrive with a of music on it.  I plugged it in and viewed the files using rhythmbox, and then I deleted them on rhythmbox not realizing that it would also delete them on my external harddrive.  So I go back into the external and I see that the files aren't actually gone, they were simply moved to a .trash-1000 folder and in there were in a folder called "info," and all the songs have been changed to .trashinfo files.  my question is how to restore them.  I am able to listen to all of these songs still on rhythmbox and itunes, but this file type is not supported by windows media player, which I need it to because I'm trying to give music to my friends.

so please help me find a course of action to take.

---

### Post by drs305 on 2010-07-12
In the .trash-1000 bin normally there are two folders, *info* and *files*. The *info* folder usually contains information about the deleted files (origin, etc), while the deleted files are in the *files* folder. If you see that folder, you should be able to copy or move your files back to the original location.

---

### Post by mikewhatever on 2010-07-12
You should be able to right click the files and select restore.

---

### Post by petewheat on 2010-07-14
The "Files" folder is empty... only the "info" folder contains files, and when I drag them into itunes, it plays those files.

---

### Post by FahadMKS on 2010-07-14
Try to copy those files to another folder in the normal Hard Disk and check if the issue gets resolved and if not restore the files by selecting option as select all and restore.

---

### Post by drs305 on 2010-07-14
If they play, then it would appear those are your deleted files or links to them. I would copy them to another location to ensure they aren't subsequently lost.

Does each file have a separate name, and are the original titles included or at least identifiable?

Are there other files in the folder which may contain the file information? A normal .trashinfo file contains information about the deleted file, such as the following when you click on it. You can look at the file size to see if the files in *info* contain actual songs.
> 
[Trash Info]
Path=images/hb1.lucid.191.fsa
DeletionDate=2010-07-11T10:44:35


You might try a universal search on your system to see if the files are duplciated somewhere else. Run the command with all your partitions mounted, and then again with all but the system partitions unmounted:
```
sudo find / -type f -iname *<filename>*
```

Example:
```
sudo find / -type f -iname *.mp3
```

---

