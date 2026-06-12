---
title: "GVFS in trash?? cant delete"
date: 2010-03-15
forum: General Help
---

### Post by spiky001 on 2010-03-15
Hi i have a folder in the trash that I cant get rid gvfs although it is empty it wont go away any ideas?

---

### Post by rsay on 2010-03-15
I have had problems with a .gvfs file in the past. I was able to get rid of it by unmounting it, rather than deleting it. It won't hurt anything to try.

```
umount -fl /home/XXXXX/.Trash/.gvfs
```

---

### Post by spiky001 on 2010-03-15
no joy with that still there I get a reply > unmount command not found?

---

### Post by kainalu on 2010-03-15
the command under linux is actually umount, with no 'n'

---

### Post by spiky001 on 2010-03-15
thks for pointing that out but still no good, it returned
> umount: /home/spiky/.Trash/.gvfs not found

Although I have been googling and have deleted it as root in local trash files but is still in trash can, I have also changed permission from root to mine still it sits there,

---

### Post by rsay on 2010-03-15
First you need to know the exact name and location of the file. The path and filename that I used were just examples.

Go to your trash directory. 

It should be here:
```
cd /home/spiky/.local/share/Trash/files
```

use the ls command to get the exact name of the file

```
ls -a *
```

Once you have the name of the offending file, and the proper path, you can try to remove it. While in the directory where the file is located, I would try the following in order:

```
rm -rf the_name_of_the_file
```
```
sudo rm -rf the_name_of_the_file
```
```
umount -fl /home/spiky/path/to/your/file/the_name_of_the_file
```
```
sudo umount -fl /home/spiky/path/to/your/file/the_name_of_the_file
```

The exact spelling, including capitalization must be correct


If one of those commands doesn't work, we'll need more information. Post the results of a command like:
```
ls -la /home/spiky/.local/share/Trash/files/*
```

Be sure to adjust the path to match the location of the file you are dealing with. You only need to post the line with the info about the file you are dealing with.

---

