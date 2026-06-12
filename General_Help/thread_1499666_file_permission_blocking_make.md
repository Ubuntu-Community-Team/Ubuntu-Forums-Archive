---
title: "file permission blocking make"
date: 2010-06-02
forum: General Help
---

### Post by harryliddic on 2010-06-02
I am trying to compile a an old linux program that is available only on Mac now. All the files and dirs are owned by root and the makefile is read only. Can some one help me untie the Gordonian knot? I've have included some pertinent info.

```
root@harry-desktop:/home/genesis/src# make all
make[1]: Entering directory `/home/genesis/src'
make[1]: Makefile.: No such file or directory
make[1]: *** No rule to make target `Makefile.'.  Stop.
make[1]: Leaving directory `/home/genesis/src'
make: *** [code_g] Error 2
root@harry-desktop:/home/genesis/src# ls -la
total 320
drwxr-xr-x 24 root root  4096 2010-06-01 22:22 .
drwxr-xr-x  3 root root  4096 2010-06-01 22:21 ..
drwxr-xr-x  2 root root  4096 2010-06-01 22:22 buffer
-rw-r--r--  1 root root 41484 2010-06-01 22:22 CHANGES
drwxr-xr-x  2 root root  4096 2010-06-01 22:22 concen
drwxr-xr-x  3 root root  4096 2010-06-01 22:22 convert
drwxr-xr-x  2 root root  4096 2010-06-01 22:22 device
drwxr-xr-x  3 root root  4096 2010-06-01 22:22 diskio
drwxr-xr-x  2 root root  4096 2010-06-01 22:22 hh
drwxr-xr-x  2 root root  4096 2010-06-01 22:22 hines
drwxr-xr-x  2 root root  4096 2010-06-01 22:22 kinetics
-rwxr-xr-x  1 root root   118 2010-06-01 22:22 libsh
-rw-r--r--  1 root root 29983 2010-06-01 22:22 Makefile
-rw-r--r--  1 root root  7036 2010-06-02 00:05 Makefile.aix
-rw-r--r--  1 root root  6946 2010-06-02 00:05 Makefile.alpha
-rw-r--r--  1 root root  5974 2010-06-02 00:09 Makefile.dist
-rw-r--r--  1 root root  5636 2010-06-02 00:05 Makefile.FreeBSD
-rw-r--r--  1 root root  8406 2010-06-02 00:05 Makefile.gamma
-rw-r--r--  1 root root  7670 2010-06-02 00:05 Makefile.hpux
-rw-r--r--  1 root root  6595 2010-06-02 00:05 Makefile.irix
-rw-r--r--  1 root root  5974 2010-06-02 00:05 Makefile.Linux
-rw-r--r--  1 root root  6560 2010-06-02 00:05 Makefile.mips
-rw-r--r--  1 root root  8128 2010-06-02 00:05 Makefile.other
-rw-r--r--  1 root root  6893 2010-06-02 00:05 Makefile.paragon
-rw-r--r--  1 root root  6343 2010-06-02 00:05 Makefile.Solaris
-rw-r--r--  1 root root  6375 2010-06-02 00:05 Makefile.sun3
-rw-r--r--  1 root root  6710 2010-06-02 00:05 Makefile.sun4
-rw-r--r--  1 root root  7324 2010-06-02 00:05 Makefile.t3d
-rw-r--r--  1 root root  6261 2010-06-02 00:05 Makefile.t3e
drwxr-xr-x  2 root root  4096 2010-06-01 22:22 newconn
drwxr-xr-x  8 root root  4096 2010-06-01 22:22 oldconn
drwxr-xr-x  2 root root  4096 2010-06-01 22:22 olf
drwxr-xr-x  2 root root  4096 2010-06-01 22:22 out
drwxr-xr-x  3 root root  4096 2010-06-01 22:22 pore
-rw-r--r--  1 root root  6137 2010-06-01 22:22 README
drwxr-xr-x  2 root root  4096 2010-06-01 22:22 segment
drwxr-xr-x  3 root root  4096 2010-06-01 22:22 shell
drwxr-xr-x  3 root root  4096 2010-06-01 22:22 sim
drwxr-xr-x  2 root root  4096 2010-06-01 22:22 ss
drwxr-xr-x  2 root root  4096 2010-06-01 22:22 startup
drwxr-xr-x  2 root root  4096 2010-06-01 22:22 sys
drwxr-xr-x  2 root root  4096 2010-06-01 22:22 tools
-r--r--r--  1 root root  1951 2010-06-01 22:22 TRANS.TBL
drwxr-xr-x  2 root root  4096 2010-06-01 22:22 user
drwxr-xr-x  9 root root  4096 2010-06-01 22:22 Xodus
root@harry-desktop:/home/genesis/src# 

```

---

### Post by rnerwein on 2010-06-02
hi
--> 
root@harry-desktop:/home/genesis/src# make all
make[1]: Entering directory `/home/genesis/src'

it's only a feeling - but your current user is root and i can see that the makefile
is designed for different operating systems and LINUX is the only OP-System i know
where root ( $HOME ) is not /  in LINUX $HOME is /root.
may be this is the part where  your makefile is getting the problem ?!
hope this can help you
ciao

---

### Post by harryliddic on 2010-06-04
The program was written in C under UNIX-linux and was in the repos until Lucid came
out. Which left me to salvage all my work by way of a disk of the program from a 1997 book on GENESIS, The program README said to copy the linux makefile to Makefile.dist which I have done. If I am in /root by mistake please tell me a fix.

---

### Post by harryliddic on 2010-06-05
I tried the following to see if the make or makefile.dist would compile but no success
Am I on the right track. This program was written to compile in Linux. Is it just Ubuntu retrictions that are blocking my way? Would I be more successful  in my old copy of Red Hat? 
```
root@harry-desktop:/home/genesis/src# chmod 777 Makefile
root@harry-desktop:/home/genesis/src# ls la
ls: cannot access la: No such file or directory
root@harry-desktop:/home/genesis/src# ls -la
total 320
drwxr-xr-x 24 root root  4096 2010-06-01 22:22 .
drwxr-xr-x  3 root root  4096 2010-06-01 22:21 ..
drwxr-xr-x  2 root root  4096 2010-06-01 22:22 buffer
-rw-r--r--  1 root root 41484 2010-06-01 22:22 CHANGES
drwxr-xr-x  2 root root  4096 2010-06-01 22:22 concen
drwxr-xr-x  3 root root  4096 2010-06-01 22:22 convert
drwxr-xr-x  2 root root  4096 2010-06-01 22:22 device
drwxr-xr-x  3 root root  4096 2010-06-01 22:22 diskio
drwxr-xr-x  2 root root  4096 2010-06-01 22:22 hh
drwxr-xr-x  2 root root  4096 2010-06-01 22:22 hines
drwxr-xr-x  2 root root  4096 2010-06-01 22:22 kinetics
-rwxr-xr-x  1 root root   118 2010-06-01 22:22 libsh
-rwxrwxrwx  1 root root 29983 2010-06-01 22:22 Makefile
-rw-r--r--  1 root root  7036 2010-06-02 00:05 Makefile.aix
-rw-r--r--  1 root root  6946 2010-06-02 00:05 Makefile.alpha
-rwxrwxrwx  1 root root  5974 2010-06-02 00:09 Makefile.dist
-rw-r--r--  1 root root  5636 2010-06-02 00:05 Makefile.FreeBSD
-rw-r--r--  1 root root  8406 2010-06-02 00:05 Makefile.gamma
-rw-r--r--  1 root root  7670 2010-06-02 00:05 Makefile.hpux
-rw-r--r--  1 root root  6595 2010-06-02 00:05 Makefile.irix
-rw-r--r--  1 root root  5974 2010-06-02 00:05 Makefile.Linux
-rw-r--r--  1 root root  6560 2010-06-02 00:05 Makefile.mips
-rw-r--r--  1 root root  8128 2010-06-02 00:05 Makefile.other
-rw-r--r--  1 root root  6893 2010-06-02 00:05 Makefile.paragon
-rw-r--r--  1 root root  6343 2010-06-02 00:05 Makefile.Solaris
-rw-r--r--  1 root root  6375 2010-06-02 00:05 Makefile.sun3
-rw-r--r--  1 root root  6710 2010-06-02 00:05 Makefile.sun4
-rw-r--r--  1 root root  7324 2010-06-02 00:05 Makefile.t3d
-rw-r--r--  1 root root  6261 2010-06-02 00:05 Makefile.t3e
drwxr-xr-x  2 root root  4096 2010-06-01 22:22 newconn
drwxr-xr-x  8 root root  4096 2010-06-01 22:22 oldconn
drwxr-xr-x  2 root root  4096 2010-06-01 22:22 olf
drwxr-xr-x  2 root root  4096 2010-06-01 22:22 out
drwxr-xr-x  3 root root  4096 2010-06-01 22:22 pore
-rw-r--r--  1 root root  6137 2010-06-01 22:22 README
drwxr-xr-x  2 root root  4096 2010-06-01 22:22 segment
drwxr-xr-x  3 root root  4096 2010-06-01 22:22 shell
drwxr-xr-x  3 root root  4096 2010-06-01 22:22 sim
drwxr-xr-x  2 root root  4096 2010-06-01 22:22 ss
drwxr-xr-x  2 root root  4096 2010-06-01 22:22 startup
drwxr-xr-x  2 root root  4096 2010-06-01 22:22 sys
drwxr-xr-x  2 root root  4096 2010-06-01 22:22 tools
-r--r--r--  1 root root  1951 2010-06-01 22:22 TRANS.TBL
drwxr-xr-x  2 root root  4096 2010-06-01 22:22 user
drwxr-xr-x  9 root root  4096 2010-06-01 22:22 Xodus
root@harry-desktop:/home/genesis/src# make 
make[1]: Entering directory `/home/genesis/src'
make[1]: Makefile.: No such file or directory
make[1]: *** No rule to make target `Makefile.'.  Stop.
make[1]: Leaving directory `/home/genesis/src'
make: *** [code_g] Error 2
root@harry-desktop:/home/genesis/src# 

```

---

