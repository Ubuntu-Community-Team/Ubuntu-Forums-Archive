---
title: "matlab can not save preference file"
date: 2010-06-11
forum: General Help
---

### Post by wdlang on 2010-06-11
Cannot write to preference file "matlab.prf" in "/home/jiangmi/.matlab/R2010a".
Check file permissions.

==========================

every time i run matlab by typing matlab in the terminal,

i see this error message

i can run some m files, but i can not use ctrl+A to copy, etc.

when i view the permission, i find below:

==================================
[EMAIL="jiangmi@jiangmi-laptop:%7E/.matlab"]jiangmi@jiangmi-laptop:~/.matlab[/EMAIL]/R2010a$ ls -rl 
 total 1368 
  -rw-r--r-- 1 root root 1265183 2010-06-05 20:04  toolbox_cache-7.10.0-2356054188-glnx86.xml 
 -rw-r--r-- 1 root root     1277 2010-06-05 20:04 shortcuts.xml 
 -rw-r--r-- 1 root root    24015 2010-06-05 20:04 Pre2009bUnixDefaults.xml 
 -rw-r--r-- 1 root  root   82133 2010-06-05 20:04 plotpickercache.xml 
 -rw-r--r-- 1 root  root    1231 2010-06-05 20:04 matlab.prf 
 -rw-r--r-- 1 root root     6525 2010-06-05 20:04 MATLABDesktop.xml 
 -rw-r--r-- 1 root root       24 2010-06-05 20:04 history.m 
 -rw-r--r-- 1 root root      14  2010-06-05 20:04 cwdhistory.m 

===================================

it is strange that in a directory under my personal directory, all the files belong to root

---

### Post by wdlang on 2010-06-11
> **wdlang said:**
> Cannot write to preference file "matlab.prf" in "/home/jiangmi/.matlab/R2010a".
Check file permissions.

==========================

every time i run matlab by typing matlab in the terminal,

i see this error message

i can run some m files, but i can not use ctrl+A to copy, etc.

when i view the permission, i find below:

==================================
[EMAIL="jiangmi@jiangmi-laptop:%7E/.matlab"]jiangmi@jiangmi-laptop:~/.matlab[/EMAIL]/R2010a$ ls -rl 
 total 1368 
  -rw-r--r-- 1 root root 1265183 2010-06-05 20:04  toolbox_cache-7.10.0-2356054188-glnx86.xml 
 -rw-r--r-- 1 root root     1277 2010-06-05 20:04 shortcuts.xml 
 -rw-r--r-- 1 root root    24015 2010-06-05 20:04 Pre2009bUnixDefaults.xml 
 -rw-r--r-- 1 root  root   82133 2010-06-05 20:04 plotpickercache.xml 
 -rw-r--r-- 1 root  root    1231 2010-06-05 20:04 matlab.prf 
 -rw-r--r-- 1 root root     6525 2010-06-05 20:04 MATLABDesktop.xml 
 -rw-r--r-- 1 root root       24 2010-06-05 20:04 history.m 
 -rw-r--r-- 1 root root      14  2010-06-05 20:04 cwdhistory.m 

===================================

it is strange that in a directory under my personal directory, all the files belong to root

the problem is solved. 

see

[https://help.ubuntu.com/community/MATLAB](https://help.ubuntu.com/community/MATLAB)

---

### Post by rajhanschinmay on 2012-06-04
Run this in terminal and it should work.

sudo chmod -R 777 ~/.matlab

Thank u.

---

### Post by rajhanschinmay on 2012-12-16
Run
sudo chmod -R 777 ~/.matlab

and / or

Replace chris with ur usernameand run
sudo chown chris /home/chris/.matlab/R2008a/matlab.prf

One of the two or both when executed will remove your error.
Thank you.

---

