---
title: "Google Earth won't install"
date: 2009-08-27
forum: General Help
---

### Post by theozzlives on 2009-08-27
K, I have Google Earth on my Laptop (specs below). I tried to install it on my AM3 and it says it won't install on AMD64, what's up?

---

### Post by P4man on 2009-08-28
You are running 64 bit ubuntu on that machine?
Im not sure there is a 64 bit versin of google earth. If not, this link may help (despite being old):

[http://ubuntuforums.org/showthread.php?t=544064](http://ubuntuforums.org/showthread.php?t=544064)

---

### Post by theozzlives on 2009-08-28
> **P4man said:**
> You are running 64 bit ubuntu on that machine?
Im not sure there is a 64 bit versin of google earth. If not, this link may help (despite being old):

[http://ubuntuforums.org/showthread.php?t=544064](http://ubuntuforums.org/showthread.php?t=544064)

I'm running 64 bit on my laptop also. The dif. is:

1. Laptop 1.73 GHz, Box 2.9 GHz
2. Laptop Intel Video, Box NVIDIA
3. Laptop Intel CPU, Box AMD CPU

---

### Post by P4man on 2009-08-28
The cpu makes no difference. The message you see " won't install on AMD64, " refers the fact the OS is 64 bit . Even on intel cpu's its called "AMD64" if you run the 64 bit versin of ubuntu. Its just the name of the architecture. If you dont believe me, run "uname -a" on your intel laptop :)

To install 32 bit apps on a 64 bit OS, you need ia32-libs

sudo apt-get install ia32-libs
edit: you probably need some other packages too, but im not sure. Google for it. Or try the above link.

---

### Post by dreamsR4living on 2009-08-28
Hmm, you could try to add the medibuntu [www.medibuntu.org](www.medibuntu.org) repository. They have the most recent version of Google Earth, which is very stable, but I am not sure if they also have a AMD 64 version...

Maybe it is worth the try...

---

### Post by 3rdalbum on 2009-08-28
> **dreamsR4living said:**
> Hmm, you could try to add the medibuntu [www.medibuntu.org](www.medibuntu.org) repository. They have the most recent version of Google Earth, which is very stable, but I am not sure if they also have a AMD 64 version...

Yes they do. Well, they have a version that installs on amd64 without hassle.

---

### Post by theozzlives on 2009-08-28
you know that's probably it. I don't think I installed medibuntu on the tower, didn't plan on watching DVDs on it.


EDIT: Now it can't connect to the server, could it be cause I'm running my web server on port 80?

---

### Post by theozzlives on 2009-09-01
Well seems nobody wants to help with my connection issue so I guess I'll just uninstall Google Earth and forget it. :(

---

