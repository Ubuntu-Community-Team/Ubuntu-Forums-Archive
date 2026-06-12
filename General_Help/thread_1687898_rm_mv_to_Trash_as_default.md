---
title: "rm: mv to Trash as default"
date: 2011-02-14
forum: General Help
---

### Post by LanguidLegend on 2011-02-14
I am running Ubuntu 10.10, and the path to my trash directory is:
~/.local/share/Trash/files

I am trying to rework the rm command in my .bashrc, to the following:
```
alias rm='sudo mv $0 --target-directory=~/.local/share/Trash/files'
```
and I keep getting this response:
mv: accessing `~/.local/share/Trash/files': No such file or directory

---

### Post by TeoBigusGeekus on 2011-02-14
Use the full path instead of ~, ie. /home/username/etc.
Mind you, you won't be able to restore the files.

---

### Post by LanguidLegend on 2011-02-14
> **TeoBigusGeekus said:**
> Use the full path instead of ~, ie. /home/username/etc.
Mind you, you won't be able to restore the files.
Really, why is that?

---

### Post by TeoBigusGeekus on 2011-02-14
Because the original path info won't be stored in the deleted file (at list in my system it doesn't).
Try this:
Delete a file normally, ie. by selecting it and then pressing delete.
Now delete a file with your rm alias.
If you go to your trash folder and right click them, only the first file will have info about its original path.

---

### Post by whatthefunk on 2011-02-14
Make sure that the folders ~/.local/share/Trash and ~/.local/share/Trash/files exist.  I think that the empty trash program simply deletes the folders.  

Also, one problem I found with setting rm as a "mv to trash" alias is  that you cant empty trash from the command line because if you rm trash,  it moves it to the trash can.  Id either set an alias like "del" that  will move files to the trash and keep rm pure or Id write a program that  will do it a little better.  

And about the file path....what it does is create a log file in ~/local/share/Trash/info  It stores path info and allows files to be restored.

---

### Post by WorMzy on 2011-02-14
This won't help with your 'sudo rm' cases, but you can use gvfs-trash instead of rm to move items to trash.

e.g.

```
gvfs-trash ~/mydocument.odt
```

---

### Post by luigi_mb on 2011-02-14
> **whatthefunk said:**
> Make sure that the folders ~/.local/share/Trash and ~/.local/share/Trash/files exist.  I think that the empty trash program simply deletes the folders.  


No, it does not.

/luigi

---

### Post by whatthefunk on 2011-02-14
> **luigi_mb said:**
> No, it does not.

/luigi

Yep.  You're right.  My empty trash program does, but the system does not.  My bad.

---

### Post by asmoore82 on 2011-02-14
> **WorMzy said:**
> This won't help with your 'sudo rm' cases, but you can use gvfs-trash instead of rm to move items to trash.

e.g.

```
gvfs-trash ~/mydocument.odt
```

Thank you, sir!

You ARE the man! :KS

Please post this to [http://www.commandlinefu.com/](http://www.commandlinefu.com/) immediately.

---

