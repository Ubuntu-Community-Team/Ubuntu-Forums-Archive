---
title: "copying all files in folder to another location"
date: 2011-02-21
forum: General Help
---

### Post by mahmoodn on 2011-02-21
suppose I have a tree structure like this:
/home/mahmood/sim/a/b/file1.cpp
/home/mahmood/sim/a/b/file2.h
/home/mahmood/sim/a/c/file3.txt
/home/mahmood/sim/d/file4.txt

How can I copy all of them to /home/mahmood/sim. So that when I run "ls" in /home/mahmood/sim, I see all files:
file1.cpp
file2.h
file3.txt
file4.txt

Can 'cp' search for all file and copy them in another folder?

---

### Post by Clever_Username on 2011-02-21
I think I can help with file1-3. The last file might be trickier though.
Here is my 2 cents for the first three files anyway.
Logged in as mahmood:
cp sim/*/*/*/*.* ~/sim

Maybe some of the pros on here can come up with a better idea.

---

### Post by mahmoodn on 2011-02-21
actually that was an example I gave. In fact the tree structure is big and I want to automate that using a script.

---

