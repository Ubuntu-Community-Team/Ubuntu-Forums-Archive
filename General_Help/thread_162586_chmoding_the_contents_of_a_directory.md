---
title: "chmoding the contents of a directory"
date: 2006-04-19
forum: General Help
---

### Post by ubuntukid on 2006-04-19
I have a directory which only the root is allowed to access. I used 'sudo chmod 777 directoryname'. Problem is that this only edits the permision of the directory and non of it's contents. Is there a command I can use with chmod which will change the permission of the folder AND all it's contents to 777?

---

### Post by cgjones on 2006-04-19
This should do it.

```
sudo chmod -R 777 *directoryname*
```

---

### Post by dave9191 on 2006-04-19
You can use the "-R" flag to recursively modify all of the contents of the directory and directories. 

sudo chmod -R 777 directoryname

Many other commands have a similar flag for applying something to all files in the dir :)

Hope that helps.

--
Dave

---

### Post by ubuntukid on 2006-04-19
That worked great. Thanks for the help.

---

### Post by David Olivier on 2006-04-19
I'm not sure you should do a chmod 777 to all files in the directory!

777 = read, write and execute for user, group and others. That may be fine for directories (though 755 or 775 might be better, so as not to give the permissions to everyone), because "executable" for a directory actually means "traversable" (the permission to go through the directory into subdirectories).

But for plain files, "executable" means really executable, and should be done only on binary executables or executable scripts.

You might set the permissions differently for files and directories:

```
cd thedir

find . -type d -exec chmod 777 {} \;

find . -type f -exec chmod 666 {} \;
```

The first "find" acts on directories, the second one on plain files. See man find.

---

