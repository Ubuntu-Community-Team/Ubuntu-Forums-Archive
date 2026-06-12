---
title: "error while loading shared libraries?!"
date: 2010-06-16
forum: General Help
---

### Post by jeremy28 on 2010-06-16
Hi all;
 
I have ubuntu 9.04 on my Virtual Machine and my host OS is Win.XP,
I've installed SSH on my linux and and now, I use PuTTY on Win.XP to connect to the SSH on linux,
 
Now, I have a problem:
When I login with "root" and run any command, I see load errors for libraries such below:
```
vim:  error while loading shared libraries: libm.so.6: cannot open shared object file: No such file or directory
ls:  error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
./shmop:  error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
…
```
I've defined a user in ubuntu and when I login with it, I have no problem in running commands!
Also, when I use "su" command in the user's session and go to the root, I have no problem again in running commands!
 
Could you help me where the problem is coming from?
Is it related to my linux version or distro?
Or anything else?!
 
TIA.

---

