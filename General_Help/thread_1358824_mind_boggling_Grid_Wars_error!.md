---
title: "mind boggling Grid Wars error!"
date: 2009-12-18
forum: General Help
---

### Post by caleb_yau on 2009-12-18
okay so i downloaded gridwars from their website. it came in a zip file in it was its executable named "gridwars." so far this seems like a pretty ordinary thing. i type at the console "./gridwars" and the error i get is 

bash: ./gridwars: No such file or directory. 

i'm definetly in the folder containing a file called gridwars. I typed it using tab completion so not only did i spell it right but it exists and is in the folder i'm currently in. I've been using linux exclusively now for a few years now and i've never seen anything like it, it makes no sense to me. Does anyone have any ideas?

btw this is the output of "file ./gridwars"

./gridwars: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.2.0, stripped

this is the output of "ls -l ./gridwars"

-rwxr-xr-x 1 sean sean 529332 2006-03-15 18:25 ./gridwars

and here's a link to the site/file 

[http://gridwars.marune.de/](http://gridwars.marune.de/)

i'm using a fresh install of 64 bit karmic.

---

### Post by blueridgedog on 2009-12-18
Do you have the 32 bit libraries installed (ia32-libs)?  Do they have a 64 bit version?

---

### Post by caleb_yau on 2009-12-18
installing ia32-libs got me a more sane error thanks! The new error is ./gridwars: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

it seems that karmic does not have libstdc++5 anymore? additionally even if it did, would it even help me? would i need a 32 bit libstdc++?

---

### Post by yavoh on 2009-12-18
I imagine they're backwards compatible?  Version 6 is in the repositories; install that and see what happens.

---

### Post by orlox on 2009-12-18
I have had this kinds of problems before, and I often found that the solution is creating the missing file as a link to the exisiting (more current) library:

```

sudo ln /usr/lib/libstdc++.so.6 /usr/lib/libstdc++.so.5

```

---

### Post by ankspo71 on 2009-12-18
Hi,
I found a link called
"How-To Fix libstdc++5 Dependency Problem in Ubuntu 9.10"
includes details for 32 bit and 64 bit.
[http://hsmak.wordpress.com/2009/12/01/how-to-fix-libstdc5-dependency-problem-in-ubuntu-9-10/](http://hsmak.wordpress.com/2009/12/01/how-to-fix-libstdc5-dependency-problem-in-ubuntu-9-10/)
Hope it helps...  I haven't tried it myself.

---

### Post by caleb_yau on 2009-12-19
orlox's fix did not help, most likely because that only fixes the 64bit library link. ankospo71's fix worked like a charm and i'm finally playing this really cool game! Thanks everyone!

---

### Post by pietro_spina on 2009-12-19
after folowing the fixes above
I get this error. any thoughts?

```
$ ./gridwars
./gridwars: /usr/lib32/libstdc++.so.6: version `CXXABI_1.3' not found (required by /usr/lib32/libGLU.so.1)
./gridwars: /usr/lib32/libstdc++.so.6: version `GLIBCXX_3.4' not found (required by /usr/lib32/libGLU.so.1)
```

-p

---

