---
title: "Terminal (ls ~ Command)"
date: 2012-02-03
forum: General Help
---

### Post by darkshadowsly on 2012-02-03
i need help figuring out how to list all content under a specific directory, when i change into the derectory i want to see all content in using 'cd' and i type 'ls ~' under that repository, the terminal list's everything under the default derectory and not in the derectory i want it to list all content, so how do i list all content using terminal in a specific folder(directroy)?

---

### Post by Dangertux on 2012-02-03
ls ~ will display the current users home directory or /root/ if root. 

Try just 

```

ls

```

---

### Post by oldos2er on 2012-02-03
I think you mean 'directory' (or folder), not repository. A repository is a server containing packages (software) available for installation. [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

If you're asking how to list (ls) files and folders recursively, use ```
ls -R
``` That will create a lot of output, which you can either page through ```
ls -R | less
``` (type **q** to exit **less**) or export the output to a text file ```
ls -R > myfolders.txt
``` which you can load into your favorite text editore and browse at your leisure.

Hope this answers your question.

---

### Post by jonobr on 2012-02-03
Hi 

May be a good idea to go over a tutorial of cli commands
like [this]("https://help.ubuntu.com/community/UsingTheTerminal").

I would recommend you read a bit as it can be frustrating if you want to do something and dont know the answer, it may give you a bad experience of terminal and ubuntu in general.

Also using the man command may help after you learn the commands

So if you type

```
 man man
```

it will give you help on the man pages

eg

```
man ls
``` will give info on ls plus options

---

