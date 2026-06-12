---
title: "Permission to write INSIDE a directory"
date: 2010-03-09
forum: General Help
---

### Post by MajinSaha on 2010-03-09
Please forgive if that sounds really stupid. But I searched in "man" and google, and nothing helped.

How do I use "chmod" command so that it allows me to write a file inside a certain directory ? This directory has permissions in the form

drwxr-xr-x

Once I try to write a file there, it says "Permission denied" ! Don't advise to use "sudo", since the file is created by some executable program compiled from a source code. If I was creating the file myself, I wouldn't have gone to this forum.

Thank you very much.

---

### Post by rnerwein on 2010-03-09
hi
not only the permissions you showed habe to work. you have to look also at:
ugo -> user, group, other thats permissions you have to look for ( the owner and the group will be shown by: ls -ld dir_name )
 but believe  me read 
this -> [http://en.wikipedia.org/wiki/File_system_permissions](http://en.wikipedia.org/wiki/File_system_permissions)
or you will never be happy on unix/linux systems.
ciao

---

### Post by ImperialXT on 2010-03-09
try chmod 775 dirname

---

### Post by ad_267 on 2010-03-09
Is the directory owned by root?

To let all users write to that directory, use:
```
sudo chmod a+w /path/to/dir
```

To make yourself the owner so you can write to it:
```
sudo chown $USER:$USER /path/to/dir
```

---

### Post by MajinSaha on 2010-03-09
Thanks a lot ! It worked. Don't know which one though, since I tried some of them at the same time.

---

