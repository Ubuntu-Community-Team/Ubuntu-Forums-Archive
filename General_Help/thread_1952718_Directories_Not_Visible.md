---
title: "Directories Not Visible"
date: 2012-04-04
forum: General Help
---

### Post by DanelectroT on 2012-04-04
I have just installed Ubuntu Server 11.10 and am having a problem.

Basic directory commands such as "cd" and "ls" are not working.
When I do a command such as ls in the root of the box, no folders/files are displayed. 
But, if i use a command such as "cd /home
This is displayed:
server@ubuntu:/home$
And an "ls" command at this point displays one folder; "server"
"cd"ing into it returns me to my root.
:server@ubuntu:~$"

Please! If anyone knows how to solve this it would be greatly appreciated if I can get some assistance. ;)

---

### Post by DanelectroT on 2012-04-04
Anyone?

---

### Post by codemaniac on 2012-04-05
First of all please check in which directory path you are standing on .
```
pwd
```.
Then ensure that the files are not hidden there .
```
ls -lat
```

---

