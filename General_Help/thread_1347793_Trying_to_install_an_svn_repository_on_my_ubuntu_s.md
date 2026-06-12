---
title: "Trying to install an svn repository on my ubuntu server"
date: 2009-12-06
forum: General Help
---

### Post by alexlesuper on 2009-12-06
So I'm following the exact steps as described here: [https://help.ubuntu.com/8.04/serverguide/C/subversion.html](https://help.ubuntu.com/8.04/serverguide/C/subversion.html)

but when I get to the step where it says that I have to enter
```
svnadmin create /path/to/repos/project
```

I get the following error:

```
svnadmin: Repository creation failed
svnadmin: Could not create top-level directory
svnadmin: Can't create directory /path/to/repos/project': No such file or directory
```

---

### Post by SuperSonic4 on 2009-12-06
Are you substituting your own directory for /path/to/repos/project?

For example for my compilation of kmess it would be ```
cd ~/SVN/kmess
```

---

### Post by alexlesuper on 2009-12-06
I'm not sure I understand the question correctly. I'm only following the instructions to the letter. When I try to do mkdir from the root it won't let me unless I sudo, so I wasn't sure if that was the right thing to do.

---

### Post by akakingess on 2009-12-06
That is the correct thing to do, but you don't need to follow the instructions to the letter, in other words, if I said create a directory for movies within your home folder by using /this/is/an/example, then you would actually use mkdir ~/movies (I hope I'm making sense).

---

