---
title: "File system problem"
date: 2011-07-25
forum: General Help
---

### Post by yconselvan on 2011-07-25
Hi everyone,

I'm facing the following strange problem. 

Sometimes when I try to remove some file the system return Input/Output error. I've checked my hard disk and everything is fine, no bad sectors.

Suddenly I have success removing the file, but now things get more strange. 

USER@HOST:~$ rm somefile.cpp
rm: cannot remove `somefile.cpp': No such file or directory
USER@HOST:~$ file somefile.cpp
somefile.cpp: ASCII C program text
USER@HOST:~$

When try to remove again somefile.cpp I can't, but if run file tool I can get properties. If I list the directory, the file doesn't appear on the list, but the file can be opened with nano.

After reboot the file have finally disappeared.

Last week every i have encountered that problem more than twice.

My system is Ubuntu Server 10.04, and I'm using LVM.

Can this be anything with LVM?

Thanks

---

### Post by galvatron408 on 2011-07-25
that happened to our production server and then a few weeks later the drive died.

i think its time to replace your drive.

---

