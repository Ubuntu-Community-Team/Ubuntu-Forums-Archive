---
title: "i can't use unity 3d on ubuntu 11.10 with nividia GeForce 7300 LE/PCI/SSE2"
date: 2011-11-23
forum: General Help
---

### Post by Gladiator-prog4me on 2011-11-23
hi 

- ubuntu 11.10 
- nividia  GeForce 7300 LE/PCI/SSE2

when i install a driver current , i can't use " unity 3d " because weh i restart my computer and log in the copmuter is freez .. mouse is moving but I can't do anything .

if i choise a nivida_173 i can use a unity 3d but i faces this problem (( Ubuntu is freezing randomly... Mouse is freezing, screen go black then appear again, mouse is moving but I can't do anything.  ))

now i use unity 2d and this working fine 

but i want to use a uinty 3d , is there are any solution ??

Thank you

---

### Post by T.exe on 2011-11-23
Because of the driver incompatibility with the kernel version ubuntu 11.10 uses.
**Correct me if I am wrong!**

Have you tried using the Nvidia (post-release updates) driver?? or the one downloaded from the Nvidia website?

---

### Post by Gladiator-prog4me on 2011-11-23
> **T.exe said:**
> Because of the driver incompatibility with the kernel version ubuntu 11.10 uses.
**Correct me if I am wrong!**


this my kernel info

```
mohamed@Mohamed-Home:~$ uname -a
Linux Mohamed-Home 3.0.0-13-generic-pae #22-Ubuntu SMP Wed Nov 2 15:17:35 UTC 2011 i686 i686 i386 GNU/Linux
```


> **T.exe said:**
> 
Have you tried using the Nvidia (post-release updates) driver?? or the one downloaded from the Nvidia website?

- yes i'am try to use ( nivdi_173 and current ) post-release updates and faces same problem 

- no i'am never download driver from  Nvidia website 

Thank you :)

---

### Post by T.exe on 2011-11-24
I was having the Unity freeze/crash problem after installing and fiddling with Compiz... and this thread really helped out
[http://ubuntuforums.org/showthread.php?t=1874630](http://ubuntuforums.org/showthread.php?t=1874630)

Have you installed anything like compiz?

And as far as your nvidia driver issue is concerned, do try out the one provided by the website.. although i am not sure if there is any difference between the community-provided graphic drivers for nvidia and the one provided by the website.

---

