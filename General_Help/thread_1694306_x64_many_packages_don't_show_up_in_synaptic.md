---
title: "x64: many packages don't show up in synaptic"
date: 2011-02-24
forum: General Help
---

### Post by Beowolf64 on 2011-02-24
Hi,
For some reason many packages don't show after I enter package names in quick  search field. I have to find each package by scrolling through the entire list. For example, typing g++ shows only some lib file, not the C++ package. The same for automake, autoconf and libtools. Synaptic works fine in 32bit ubuntu.

What is going on?

---

### Post by dino99 on 2011-02-24
try:
sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a
sudo dpkg-reconfigure synaptic

sidenote: only use 64 bits if you are a coder
[http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now](http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now)

---

### Post by Jouke74 on 2011-02-24
I noticed the same thing. The point of the Quick search IMHO is to filter out the results after you have already searched. So first click Search and type e.g. "rar". This will still give quite a lot of packages listed. Now to find the Rar program in the list use quick search subsequently. 

The package list seems too big for quicksearch to straight find everything at once.

---

### Post by Beowolf64 on 2011-02-24
It's it a bug or a feature? Most of the packages use x86 binaries only. Maybe the synaptic manager is setup to show binaries for x64 targets only?

---

