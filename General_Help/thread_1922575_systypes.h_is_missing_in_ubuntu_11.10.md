---
title: "sys/types.h is missing in ubuntu 11.10"
date: 2012-02-09
forum: General Help
---

### Post by jacob.david on 2012-02-09
[FONT="Verdana"]Could someone please tell me which package has the sys/types.h. I'm running ubuntu 11.10 and the entire sys directory is missing. I already have glibc6 and glibc6-dev installed. I even tried to reinstalling it but still the sys directory is not present.[/FONT]

---

### Post by Doug S on 2012-02-09
If you install the build essential stuff, you should end up with sys/types.h```
sudo apt-get install build-essential
```

---

### Post by jacob.david on 2012-02-09
I installed the package and still couldn't find it. However I can see /usr/include/x86_64-linux-gnu/sys/types.h. But I'm trying to compile a program that is looking for /usr/include/sys/types.h. Trying to google what is the difference between these two.

---

### Post by jacob.david on 2012-02-09
OK. I have finally figured it out and posting it here as it may help someone someday. Basically by default only the 64 bit libraries are included and all the header files goes info /usr/include/x86_64-linux-gnu (although the header files are same for 32 bit and 64 bit). These are part of debian package lib6-dev. If you want the 32 bit libraries then install the package libc6-dev-i386. This package creates /usr/include/sys along with other ones. However the headers are soft linked to /usr/include/x86_64-linux-gnu/sys.

---

### Post by jacob.david on 2012-02-09
[FONT="Courier New"]
$ dpkg -S /usr/include/sys/types.h 
libc6-dev-i386: /usr/include/sys/types.h
$ dpkg -S /usr/include/x86_64-linux-gnu/sys/types.h 
libc6-dev: /usr/include/x86_64-linux-gnu/sys/types.h
[/FONT]

---

### Post by karthiks840 on 2012-02-11
Hi,

I have installed lib6c-dev package....but still I get errors like 

> error: sys/types.h: No such file or directory

Pls help...
i am trying to compile Android Source... but got stuck here... :( :(

---

### Post by jacob.david on 2012-02-12
[FONT="Verdana"]Sorry but I'm not familiar with Android source. Can you try installing the libc6-dev-i386 package and see how it goes? [/FONT]

---

