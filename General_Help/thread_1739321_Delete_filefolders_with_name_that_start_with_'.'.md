---
title: "Delete file/folders with name that start with '.'"
date: 2011-04-25
forum: General Help
---

### Post by Harmonicon on 2011-04-25
Currently I am doing a java project and I renamed some file/folders to start with '.'. 
i.e. ".project", ".classpath", ".settings/"

I can see them on my desktop but i cannot delete them. In the terminal, "ls" command does not show these files exist. "rm" will also say cannot find these files. How do I get rid of these files/folders?

Thank you.

---

### Post by bodhi.zazen on 2011-04-25
```
ls -A
```

will list them

```
rm ./.file
```

will remove them

if it is a directory, use the -rf

```
rm -rf ./.directory
```

Of course you may need to CD into the proper directroy first

```
cd ~/Desktop
```

---

### Post by Timmer1240 on 2011-04-25
when you put a . in front of a file it becomes a hidden file all you have to do is open the desktop folder as administrator then delete the files I believe that will work

---

### Post by yetiman64 on 2011-04-25
> **Timmer1240 said:**
> when you put a . in front of a file it becomes a hidden file all you have to do is open the desktop folder **as administrator** then delete the files I believe that will work

Hidden files don't need to be deleted as administrator if they are in the users home directory (as the Desktop is), otherwise bodhi.zazen's commands would have needed sudo before them (they don't though :)).

You are right that the period (.) before the file indicates the files are hidden. 

"ls -A" will show them in terminal or CTRL + H while in the folder containing them will show them in the GUI. No need to open as administrator, unless the files and/or the folder they are in are owned by root.

Limiting using "open as Administrator" or root access (with sudo) to only when absolutely necessary is a good practice to get into (ie. in some circumstances using root access when unneeded can cause serious problems if certain files get their ownership/permissions changed accidentally -- here's looking at you ".ICEauthority"). .ICEauthority is in the user's home folder btw.

---

