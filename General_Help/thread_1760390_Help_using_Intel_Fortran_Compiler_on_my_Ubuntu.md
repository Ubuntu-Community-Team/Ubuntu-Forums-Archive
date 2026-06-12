---
title: "Help using Intel Fortran Compiler on my Ubuntu"
date: 2011-05-16
forum: General Help
---

### Post by apil.tamang on 2011-05-16
Hi whoever is reading this,

I recently installed the intel R Fortran Compiler on my system. I'm using eclipse as my IDE for writing some fortran codes for my research. When I try to build the source file using the intel compiler, the IDE reports the failure to find 'ifort', which is understandable.

The process to using ifort involves some steps:
1. In the terminal, enter     : $ source install-dir/bin/compilervars.sh  intel64 

2. Then to invoke the compiler: ifort (options...)

Steps 1 and 2 let me call ifort from the terminal. However, as soon as I exit the terminal and restart it (the terminal) I need to follow 1 and 2 again. In other words, I can not seem to set the path for ifort in a normal way. I do not understand the implication of the command "source" very well either, or the way step 1 has been setup. Can someone advise me on a way to modify settings such that the IDE (eclipse) can access 'ifort' anytime?

---

