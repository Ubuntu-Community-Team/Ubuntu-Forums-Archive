---
title: "Can't write to My Documents"
date: 2010-03-06
forum: General Help
---

### Post by timg1982 on 2010-03-06
Hi,
I have installed Jaunty on my laptop. I have a dual boot with Windows 7 and I've set up access to my windows partition. I can read and write to the music and photos directories but I can't write anything to My Documents in the windows file system. I have tried in Gnome and from a terminal and checked that I have write permissions set correctly.

For example in the My Documents directory:
```

$ mkdir test
mkdir: cannot create directory `test': Operation not supported

```

I get the same message if I try to rename My Documents using either mv in the terminal or the Rename option in gnome.

Thanks for any help,

Tim

---

### Post by ajgreeny on 2010-03-06
How did you set the access you say you have to the windows drive?  It sounds as if there is a problem with permissions in some way, so look at the output of the terminal command ```
ls -al
```on the My Documents folder in windows.  I am assuming that will give the same sort of output as it would on a linux folder, but as I don't have windows any more, I can't check that.

You can also use nautilus to navigate to the folder and files in it and xcheck permissions with a *right click ->properties*

---

### Post by timg1982 on 2010-03-06
I set it up using NTFS configuration tool so that it's mounted at startup.
ls -al shows that everyone has read, write and executable permissions on the directories:
```

drwxrwxrwx 1 root root      0 2010-03-06 19:27 My Documents

```
The owner is root but even when I use sudo I get the same error message. Also (as I mentioned above) I can write to the Music and Photo folders with no problems. They are all on the same partition and were mounted under the same mount point (/windows).

Thanks,

Tim

---

### Post by MichealH on 2010-03-06
It could be because the new library system in Windows 7 it runs on XML so It may not give you permissions to use it.. Even if its locked

---

### Post by timg1982 on 2010-03-06
I think I've found what's going on. My Documents is actually a link of some sort to the Documents (both on the windows partition) folder although Ubuntu doesn't recognise this. If you write to the documents folder it will also show up in My Documents. No idea why this happens but it seems to work.
Tim

---

