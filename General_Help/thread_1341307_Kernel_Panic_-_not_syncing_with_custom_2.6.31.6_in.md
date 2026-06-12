---
title: "Kernel Panic - not syncing with custom 2.6.31.6 install on Debian5"
date: 2009-11-29
forum: General Help
---

### Post by Quarg on 2009-11-29
I've got a debian 5 box which I'm trying to put a custom linux kernel onto. I compiled it, made a kernel and initrd, modified the GRUB loader, and now, when i try to boot it off of that kernel, i get this:

[ 0.929069] Kernel Panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0) 
root (hd0, 0)

I googled around, but couldn't find anything that worked. 
Thanks for any help

---

### Post by falconindy on 2009-11-29
Could be a lot of things. What was your base .config that you started with? What changes did you make?

Compiling a kernel isn't like tying your shoes.

---

### Post by Quarg on 2009-12-06
Sorry it's taken me so long to reply--

The base config I started with was what was already there -- that is, I did the make menuconfig for the ncurses interface and just exited so that it saved one. Then I changed the ext2 option to y and recompiled it when I got that error message.

---

