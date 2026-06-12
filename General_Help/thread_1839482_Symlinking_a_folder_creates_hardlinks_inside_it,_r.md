---
title: "Symlinking a folder creates hardlinks inside it, right?"
date: 2011-09-05
forum: General Help
---

### Post by Bladtman242 on 2011-09-05
I've symlinked to a folder in my dropbox, using "ln -s foldername" outisde of the dropbox folder.
By running ls -l inside the new folder, you can see that the new files aren't synlinks. ("-" instead of "l")
Seeing as they work kind of like symlinks i assumed they are hardlinks, and what do you know they have the same inodes :)
However: running a "ls -li" gives me this:
```
771443 -rw-r--r-- _***1***_ bladt bladt    0 2011-09-05 21:38 README.TXT

``` (I've highlighted the "1", that should indicate that only one link to this file exists) 

Even though another file with the same inode exists in another folder?
What does this all mean?

Thanks a bunch in advance :)

---

### Post by wt8008 on 2011-09-05
I don't believe any hard links are created. You can think of your symlink as just a name or label which references the original directory as-is.

---

### Post by Bladtman242 on 2011-09-05
Hmm, I hadn't thought about that. 
So the files aren't displayed as symlinks because when I cd into the folder (which is really a symbolic link) i see the actual files. No links except the folder link is ever created? 

That certainly would explain it. 
Thank you :)

---

### Post by wt8008 on 2011-09-05
> **Bladtman242 said:**
> Hmm, I hadn't thought about that. 
So the files aren't displayed as symlinks because when I cd into the folder (which is really a symbolic link) i see the actual files. No links except the folder link is ever created? 

That certainly would explain it. 
Thank you :)

I think you got the idea.

If you want to do an experiment try changing the names in one of the folders, you can then see the file name also gets changed in the other folder. Then you can see that they are exactly the same folder, and not just links to the files.

---

### Post by Bladtman242 on 2011-09-06
where as renaming the actual file would break symbolic links (if there had been any) to that file.
I think I get it, thanks a bunch :)

---

