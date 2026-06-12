---
title: "How to browse hidden files on ubuntu"
date: 2012-04-10
forum: General Help
---

### Post by JuanMC on 2012-04-10
If someone could help me with this ill really appreciate it. I have a file system with two hidden directories, i need to browse the files that are inside those two directories, the problem is that the directories names are '.' and '..', how can i acces them.

---

### Post by WorMzy on 2012-04-10
In some graphical file managers, pressing Ctrl+H will toggle the visibility of "hidden" files and folders.

If this doesn't work in the file manager you're using, look in the view menu for a "show hidden files/folders" option.

Alternatively, open a terminal, and browse to the directory with cd.

e.g.

```
cd /home/username/.hiddenfolder
```

then open your file manager from there. e.g.

```
nautilus
```

---

### Post by HotForLinux on 2012-04-10
What have you tried?
"." means the directory itself and ".." the parent
To list the contents of a directory, including hidden files, use the commands:
"**ls -a**" or "**ls -la**"
In nautilus filemanager, to see the hidden files press Ctrl-H

---

### Post by JuanMC on 2012-04-10
The problem is that if i do cd .. it will bring me to the previous directory, and .. its actually the name of the folder that i want to browse, any idea how can i do this?

---

### Post by WorMzy on 2012-04-10
How did you create these directories? Can you cd in to the directory containing these directories, then post the output of ```
ls -la
```

---

### Post by JuanMC on 2012-04-10
I didnt create them, someone else did. If i do ls -alh i get this result: 

root@luis-laptop:/home/luis/Desktop/fsys/lost+found# ls -alh
total 13K
drwxrwxrwx 2 root root  12K 2012-04-10 15:46 .
drwxrwxrwx 3 luis luis 1.0K 2012-04-10 15:46 ..

---

### Post by WorMzy on 2012-04-10
Like HotForLinux said, those are just links to the parent directory and the current directory. Every folder has those automatically, there's nothing "inside" them in the way that you're suggesting.

---

### Post by HotForLinux on 2012-04-10
If you put things inside "fsys" you will see that the link "..", inside lost+found, "gets bigger".

---

### Post by HotForLinux on 2012-04-10
> **JuanMC said:**
> I didnt create them, someone else did. If i do ls -alh i get this result: 

root@luis-laptop:/home/luis/Desktop/fsys/lost+found# ls -alh
total 13K
drwxrwxrwx 2 root root  12K 2012-04-10 15:46 .
drwxrwxrwx 3 luis luis 1.0K 2012-04-10 15:46 ..


The numbers 2 and 3 mean:
1) the directory ".", which is lost+found, has 2 things inside, which are the links to its parent (..) and to itself (.)
2) the directory "..", which is "fsys", has 3 things inside, which are the links to its parent (..) and to itself (.) plus the directory lost+found


Make a directory wherever you can (with nautilus or with the command "mkdir *my_new_directory"*) and explore its contents with "ls -la". You will see again two files: "." and "..", which are links to the directories: itself and parent.

---

