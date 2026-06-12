---
title: "Can't delete/rename file"
date: 2010-02-06
forum: General Help
---

### Post by underquark on 2010-02-06
I have moved all files from one hard drive to another but one file remains that I cannot move, delete or rename.


From a fresh boot, nothing nefarious running in the background...

Using Nauitilus, find a file called:
.goutputstream-59R62U

It appears to be a 1.5Gb MPEG file.  I can click on it and it plays in MoviePlayer.  I can drag it into VLC and it plays normally. But I can't move it, delete it or rename it and I can't do the same to its parent directory or the parent of that directory.


Running sudo nautilus from Terminal it doesn't appear at all.


Running Gnome Commander it doesn't show up either.  When trying to delete its parent directory (with permissions set to rwxrwxrwx) I get the following error:

Error while deleting ".goutputstream-59R62U"

File not found



It's tiny, it's not an especially great movie but it's annoying. Any help appreciated.

---

### Post by pbrane on 2010-02-06
Have you tried **sudo rm -fr .goutputstream-59R62U** while in the same directory as the file? Since this appears to be a hidden file you shouldn't need the *r* option, but it won't hurt. If that works you should be able to rm the parent directory the same way.

If that doesn't work could you post the results of **ls -al *parent_directory*** where *parent_directory* is the parent directory of the file you wish to remove.

Also post the output of **file .goutputstream-59R62U**

---

### Post by underquark on 2010-02-06
Thank you very much.  **cd**'d to the directory in question and **ls** couldn't see the file  but **sudo rm -fr .goutputstream-59R62U** removed it.

---

### Post by SuperSonic4 on 2010-02-06
ls didn't see it because it's a hidden file. It would have spotted it if you'd passed the -a or -A options with ls

---

### Post by underquark on 2010-02-06
Thank you. I'll mark this one as [solved].

---

