---
title: "Rsync help"
date: 2010-03-13
forum: General Help
---

### Post by jfmanamtr on 2010-03-13
I am trying to use rsync & ssh to move a backup folder some computers to a server. I found a command that is supposed to do this, but I am having issues getting it to work.

```
rsync -avz -e 'ssh -p 'port' 'username'@'hostname' ' /source/path host:/destination/path
```

so, I am needing some help to this. Any ideas?

~John

---

### Post by jfparis on 2010-03-14
Your command line seems a bit complicated and usually you don't need the -e 'ssh -p 22' part if you are running it from a unix/linux computer

So usualy I run someting like that:

```
rsync -az --del --progress /home/xxx/ jfparis@toto.com:/home/xxx/backup/ 
```

You need to be really carefull with the trailing '/' on the paths as rsync gonna have different behaviours depending on whether they are present or not.

---

### Post by jfmanamtr on 2010-03-14
I have to have the -e 'ssh -p PORTNUMBER'. I don't use the standard port. What is the difference with the trailing slash?
 
~John

---

