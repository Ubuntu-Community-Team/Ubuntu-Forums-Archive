---
title: "'no such file' error despite presence of file"
date: 2010-10-18
forum: General Help
---

### Post by shadowofgrael on 2010-10-18
I just installed a program and do not know what is causing this error.
When I run it from the applications menu I get the following error "Could not launch 'FirstClass Client' :Failed to execute child process "/opt/firstclass/fcc" (No such file or directory)". I opened up a terminal and looked at the location. The file is there.
I do not know much at all in this area but do not understand why this error is occurring. Any help would be nice.

Terminal output: <will@will-Latitude-E6400:/opt/firstclass$ ls -al
total 15128
drwxr-xr-x 10 root root    4096 2009-11-18 13:22 .
drwxr-xr-x  3 root root    4096 2010-10-18 17:51 ..
drwxr-xr-x  3 root root    4096 2009-08-06 01:15 download
-rw-r--r--  1 root root     867 2009-11-18 12:29 fcapps
-rwxr-xr-x  1 root root 7521991 2009-11-18 13:22 fcc
-rwxr-xr-x  1 root root 5315334 2009-11-18 13:22 fccicons.rez
-rw-r--r--  1 root root 2587680 2009-11-18 13:22 fcc.rez
drwxr-xr-x  3 root root    4096 2009-08-06 01:15 fcctemp
-rw-r--r--  1 root root     141 2009-11-18 12:29 fcfonts
drwxr-xr-x  3 root root    4096 2009-11-18 13:22 fcp
-rw-r--r--  1 root root   10281 2009-11-18 12:29 firstclass.png
drwxr-xr-x  3 root root    4096 2009-08-06 01:15 Images
drwxr-xr-x  3 root root    4096 2009-08-06 01:15 plugins
drwxr-xr-x  3 root root    4096 2009-11-18 13:22 settings
drwxr-xr-x  6 root root    4096 2009-11-18 13:22 .svn
drwxr-xr-x  3 root root    4096 2009-11-18 13:22 tools>

---

### Post by ubername on 2010-10-18
Where do you see the error message when you launch it from the application menu? Does a new window pop up?

---

### Post by spikoley on 2010-10-18
What happens when you run it from the command line?  You might need to put sudo or gksudo before the command.

```
/opt/firstclass/fcc
```

---

