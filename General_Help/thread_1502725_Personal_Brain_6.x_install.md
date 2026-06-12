---
title: "Personal Brain 6.x install?"
date: 2010-06-05
forum: General Help
---

### Post by gregg_hughes on 2010-06-05
Good afternoon, all!

I'm trying to install Personal Brain 6.0.1.5 into the netbook edition of Ubunto 10.04 and having no luck.  Various sudo combinations to execute the shell script aren't working - either the file doesn't exist or I don't have ability to do so.

Any hints?

Thanks!


Gregg

---

### Post by prshah on 2010-06-05
> **gregg_hughes said:**
> either the file doesn't exist or I don't have ability to do so.

sudo gives you the ability. So that's not your problem.

I would say that your first guess on correct. In linux, filenames are case sensitive, so Install.sh, INSTALL.SH, install.sh and Install.SH are all different filenames, unlike as in Windows. So that first thing you need to check is case.

Second, executables in linux can only be executed with the path. Eg, to run an executable in the current directory, you need to use the command with a "./" preceeding it. If in another directory, include the entire path eg```
./install.sh #current directory
~/Desktop/install.sh
/home/gregg/Desktop/install.sh
```

If you still cannot get it to work, please post back more details including the type of file, location, etc. A directory listing showing the file in question would be helpful (hint: use "ls -l" for long /detailed directory listings)

---

