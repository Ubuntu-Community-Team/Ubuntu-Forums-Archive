---
title: "Basic Postgresql location question"
date: 2010-08-02
forum: General Help
---

### Post by MikeyDL on 2010-08-02
I've been working with a Postgresql and trying to struggle through the installation and usability of that database in Ubuntu.  I was getting ready to work through the tutorials when I saw that you had to make (i.e. compile) and install them from your base directory.  However, the commands to do so had the following:

$ cd ..../src/tutorial

So basically they don't give you a clue where anything is located.  Still struggling with directory structure so was wondering if anyone here knows where the tutorial files are located in Ubuntu from a repository install.

---

### Post by MikeyDL on 2010-08-02
Oh and I was trying to do a basic find command to find the directory and pieced together this 

```
find -name tutorial -type d
```

but i'm not really sure how to use the find command.

---

### Post by gmargo on 2010-08-02
The tutorial files are included in the **postgresql-doc-8.4** package, in the 
/usr/share/doc/postgresql-doc-8.4/tutorial/ directory.

---

### Post by MikeyDL on 2010-08-03
Thanks for that tip.  I didn't find it at first, then I clue'd into the fact that I also needed to install the documentation package from the repo! 

Now I"m a happy camper :-)

---

