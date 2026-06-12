---
title: "example on the &quot;find&quot; man page is not working"
date: 2010-09-18
forum: General Help
---

### Post by acastro on 2010-09-18
Hello,

I have a project I'm working on. I checked it out from Subversion and now on my root folder I have several folders with projects and sub projecs. I wanned to do a script that will update all the projects in a single command. Now, the project is growing and some new projects are added, folders inside the projects and so on, so I didn't want to make a list of static paths to update.

I was rather trying to create a script that will go into all the subfolders, then find the parent directories and so a 'svn up' on those.

So what I was trying to do was to look for folders containing a ".svn" folder and update those. The problem is that currently my project has 888 of such ".svn" folders, but only 10 of them are real parent folders, so it will be quite slow and inefficient to an 'svn up' for each folder.

Reading the man pages of the 'find' command I found the very last example which said this:

> 
find repo/ -exec test -d {}/.svn -o -d {}/.git -o -d {}/CVS ; \
-print -prune

Given the following directory of projects and their associated SCM administrative directories, perform an efficient search for the projects' roots:

       repo/project1/CVS
       repo/gnu/project2/.svn
       repo/gnu/project3/.svn
       repo/gnu/project3/src/.svn
       repo/project4/.git

In this example, -prune prevents unnecessary descent into directories that have already been discovered (for example we do not search project3/src because we already found project3/.svn), but ensures sibling directories (project2 and project3) are found.


That seemed to be pretty similar to what I was looking for, so I try it (without the git and CVS part) but I get this error message:

> 
acastro@pi:~$ find myproject/ -exec test -d {}/.svn ; -print -prune
find: missing argument to `-exec'
No command '-print' found, did you mean:
 Command 'nprint' from package 'ncpfs' (universe)
 Command 'print' from package 'mime-support' (main)
 Command 'wprint' from package 'wprint' (universe)
 Command 'qprint' from package 'qprint' (universe)
-print: command not found


Now I have no idea what this may be the problem here. Is there an error in the command I am trying to execute of there's an error with the documentation of the "find" command?

Thanks for your help

---

### Post by acastro on 2010-09-18
FIXED!

After looking a little bit further, I found this post: [http://www.devdaily.com/linux/unix-linux-find-error-missing-argument-to-exec](http://www.devdaily.com/linux/unix-linux-find-error-missing-argument-to-exec)

So, basically I needed a / before my ;, like this:

```
find . -exec test -d {}/.svn \; -print -prune
```

---

