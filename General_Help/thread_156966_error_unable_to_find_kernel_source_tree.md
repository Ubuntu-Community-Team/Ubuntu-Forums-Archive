---
title: "error: unable to find kernel source tree"
date: 2006-04-08
forum: General Help
---

### Post by piccolo solo on 2006-04-08
Im installng nvidia LAN & audio drivers. getting this error. I've found a number of resources to try to solve this - but getting lost. As I understand it I need to download and/or install source kernal to a directory and point the installer to it - can't get to grips with exactly what to do. I've attached the nvidia installer log that gives error details.

there is nothing in /usr/src
can someone guide me please.

many thanks
Piccolo

---

### Post by xenmax on 2006-04-08
I am not exactly sure, but if you search in Synaptic for kernel source or linux source , you may find some packages. Try installing the one that corresponds to your kernel. To find you kernel version, type in terminal.
```
uname -r
```

---

### Post by piccolo solo on 2006-04-08
thanks for replying xenmax. I seem to have got somewhere (don't know how) but now I'm getting gcc version errors. it seems I need gcc 3.4 but I have gcc 4. how do I install (rollback) to 3.4

thanks
Picc

---

### Post by xenmax on 2006-04-08
I had this once too. I just installed the required version of gcc, while still keeping gcc 4.0 which came with build essential. That worked for me, no other tweak, setting. But i have seen in other threads, people suggesting exporting some variable to indicate version needed... search in forums for something like [keywords: export CC]..

Well i did the search: 
```
CC=gcc-3.4
export CC
```

---

### Post by piccolo solo on 2006-04-08
thanks

but i dont think that version 3.4 is installed. so using your code example seems to change a label but not use another version? when I enter
gcc -v

it returns version 4.0.2, regardless of whether I have changed CC to 3.4 or back to 4 again.

when I leave it with version 4 I get a bit further with compiling. then it stops and says "not compiled"

I think I actually need to download and install earlier version
How do I do this

thanks
Picc

---

### Post by xenmax on 2006-04-08
Well, sorry if i was not clear, but i suggested installing the required version of gcc and then trying that code...

---

### Post by piccolo solo on 2006-04-08
but how do I install it? It is not listed in Synaptic. Where do I get it from?

thanks

---

### Post by xenmax on 2006-04-08
Well, i certainly see gcc-3.4 listed in my Synaptic. Its listed under Development section(will also be visible under All) - so it should NOT be a case of not having universe/multiverse enabled in your sources... but i could be wrong. Did you do a search  in Synaptic?

---

### Post by piccolo solo on 2006-04-08
yes I've searched.
it lists:
gcc                     4:4.0.1-3
gcc-3.3-base         1:3.3.6-8ubuntu1
gcc-4.0                 4.0.1-4ubuntu9
gcc-4.0-base         4.0.1-4ubuntu9

that's all

I've found this [ftp://ftp.mirrorservice.org/sites/sources.redhat.com/pub/gcc/releases/gcc-3.4.0/](ftp://ftp.mirrorservice.org/sites/sources.redhat.com/pub/gcc/releases/gcc-3.4.0/)

but I don't know which archive to download nor how to install it. bear in mind that I am d/loading to USB drive and transferring it to ubuntu box. (cos I cant get online with linux till I install my drivers!)


thanks
Picc

---

### Post by piccolo solo on 2006-04-08
OK i've downloaded 2 tars - don't know whether to use gz or bz2? I guess I'll figure it out eventually!

---

