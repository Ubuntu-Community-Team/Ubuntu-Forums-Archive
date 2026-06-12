---
title: "Cannot access subfolders in my home folder with the terminal"
date: 2010-05-10
forum: General Help
---

### Post by dbfuru on 2010-05-10
I am a relatively new user of Ubuntu and am using the 64bit version of Ubuntu 10.04.

Now I can access the folders in my home folder through the places GUI, but I can't access them in the terminal. When I begin typing in the terminal and press tab it does not autocomplete, and typing the directory manually says that there is no such file or directory, even though when I type dir or ls they are clearly there.

Thanks in advance.

---

### Post by nothingspecial on 2010-05-10
What are you typing and where are you trying to get to?

---

### Post by Grenage on 2010-05-10
so if in nautilus you go to:

/home/***username***

and in the terminal you go to:

/home/***username***

The folders are different?

---

### Post by dbfuru on 2010-05-10
Ok, I type cd and end up at 

jake@Jakes-Computer:~$ which I assume is my home folder. If I type dir I can see:

jake@Jakes-Computer:~$ dir
Desktop    Downloads         Music     Public      Videos
Documents  examples.desktop  Pictures  Templates

When I type, say cd documents: 

jake@Jakes-Computer:~$ cd documents
bash: cd: documents: No such file or directory

Edit: In Nautilus I can access all the directories, make new folders, etc, but in the terminal I can't even change to those folders.

---

### Post by nothingspecial on 2010-05-10
Documents starts with a capital D.

Bash is case sensitive

```
cd Documents
```

---

### Post by dbfuru on 2010-05-10
You've got to be kidding me!

Wow.. That was a silly mistake.. Thanks a lot though!

---

### Post by Grenage on 2010-05-10
Also, it's worth using *ls* for a directory list, rather that *dir*.  I'm assuming that Ubuntu has included that to help Windows users, but it likely won't work on other distros.

---

### Post by nothingspecial on 2010-05-10
No problem :P

---

