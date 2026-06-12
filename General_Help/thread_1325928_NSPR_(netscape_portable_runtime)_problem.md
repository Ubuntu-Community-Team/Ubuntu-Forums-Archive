---
title: "NSPR (netscape portable runtime) problem"
date: 2009-11-13
forum: General Help
---

### Post by jaytron on 2009-11-13
I'm trying to compile an app that makes use of the nspr library. I'm running into an error though with this part of the make file:

g++ -ljs -lboost_thread-mt -lboost_regex -lboost_system-mt -lnspr -lxerces-c -lmysqlpp   -c -g -I/usr/local/include/boost-1_38/ -I/usr/local/include/mysql++ -I/usr/include/mysql -I/usr/local/include/nspr -I/usr/local/include/boost -I/usr/local/include/js -MMD -MP -MF build/Debug/GNU-Linux-x86/resources/constants.o.d -o build/Debug/GNU-Linux-x86/resources/constants.o resources/constants.js
g++: resources/constants.js: linker input file unused because linking not done

Looking around on google, it seemed the -c flag could be causing the problem, so when I take that out, I get this:

 g++ -ljs -lboost_thread-mt -lboost_regex -lboost_system-mt -lnspr -lxerces-c -lmysqlpp    -g -I/usr/local/include/boost-1_38/ -I/usr/local/include/mysql++ -I/usr/include/mysql -I/usr/local/include/nspr -I/usr/local/include/boost -I/usr/local/include/js -MMD -MP -MF build/Debug/GNU-Linux-x86/resources/constants.o.d -o build/Debug/GNU-Linux-x86/resources/constants.o resources/constants.js
/usr/bin/ld: cannot find -lnspr
collect2: ld returned 1 exit status

I'm not sure what the issue is. Ive installed nspr through the synaptic installer, and by compiling from source (via make install). nspr shows up under my usr/include. Any ideas? I'm doing this on Ubuntu 8.10

Thanks in advance for any help

---

### Post by jaytron on 2009-11-13
Actually I was able to solve it by replacing -lnspr with -lnspr4, but now I have  new problem. I'll post a new thread for that. Thanks

---

