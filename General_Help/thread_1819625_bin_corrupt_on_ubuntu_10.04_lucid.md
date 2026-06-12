---
title: "/bin corrupt on ubuntu 10.04 lucid"
date: 2011-08-06
forum: General Help
---

### Post by deniro on 2011-08-06
How can I repair /bin or replace it
using ubuntu 10.04 lucid 64-bit
I have live cd.
Commands like /bin/ls or /bin/chmod are corrupt.
 
thx
deniro--

---

### Post by ~!geek!~ on 2011-08-06
I don't get you, what exactly do you mean when you say /bin binaries are corrupt?
You could have provided the output of *corrupt commands, if possible.

Anyways you may check if this is not because of permission changes of /bin directory. 
From what I know about permissions of /bin directory,
1) /bin has a permissions 755 by default (i.e. rwxr-xr-x).
2) The binary programs  in /bin which are  symbolic links, i.e. orginal files are in some other directory say in boot, etc or lib directories have the file permissions as 777 (i.e. rwxrwxrwx). 
3) The directory /bin is owned by root.
So its quite safe to check if this is the case with the /bin you are having problems with.

You may check if using sudo you are able to use ls command.
or  

For another quick check, you may try 
> sudo chmod 755  /bin/ls
After this try to execute ls command for some directory. If you are able to get expected output, your target should be to set permissions as mentioned above (please refer some other article too before assuming all three permissions mentioned above to be absolutely correct. They r correct only to the extent I know)

If above steps don't help u, you may have to backup original /bin directory (backing up is always good) and copy /bin from live cd to /bin of the corrupt /. Again check for the permissions. (Before attempting this copying thing, consult some other articles too. It may be dangerous for the stability of the system you originally having)

---

### Post by deniro on 2011-08-06
thanks for the reply..
yes some of the  files under /bin are really correupted somehow.
I copied from live cd /bin  to /bin
with this looks like  some of them seem to be fixed fixed. but not all files are in /bin dir of livecd
 
now I am having problem with date command
date  file is corrupt and when I type it;
I see some  garbage characters and "ELF: not found" message"
 
so I need to replace /bin/date from somewhere
 
what is the package name for date command so that I can install with apt-get install comand (with live cd boot)
 
Thx
deniro--

---

