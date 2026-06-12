---
title: "See what process is doing ?"
date: 2010-04-05
forum: General Help
---

### Post by xx77aBs on 2010-04-05
Hello :) I have one computer that has installed Ubuntu 9.10, lighttpd, php and that stuff, so it can be used as web server and other things :D 

Anyway, today I logged via SSH and my load was ybout 1.5 ... so I typed htop to see what is happening, and all I can see is one process created by www-data user (lighttpd) and it's using 100% CPU ...

I'm not only one on the server, but I'm the admin, so is there any way to see little more details about that process ? Like what is it doing (is it using files from hard disk, or maybe connected to some URL or something) so I can know if it's just zombie process that I need to kill, or maybe it's doing something usefull :)

Thanks !

---

### Post by john newbuntu on 2010-04-05
One quick way to find out is to attach to the process using "strace".

strace -p 1234
assuming 1234 to be the processid

Mind you you will have a ton of data being dumped on screen.  You can always hit ctrl-c to get out of strace.

---

### Post by iponeverything on 2010-04-05
```
sudo lsof -p <pid> 
```

might also give an idea of what its doing.

---

### Post by xx77aBs on 2010-04-05
> **john newbuntu said:**
> One quick way to find out is to attach to the process using "strace".

strace -p 1234
assuming 1234 to be the processid

Mind you you will have a ton of data being dumped on screen.  You can always hit ctrl-c to get out of strace.


thanks, but this isn't returning anything :)

> **iponeverything said:**
> ```
sudo lsof -p <pid> 
```

might also give an idea of what its doing.

Thanks !! Now I know who is running it :)


any other ideas?

---

