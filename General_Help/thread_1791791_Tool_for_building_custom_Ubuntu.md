---
title: "Tool for building custom Ubuntu"
date: 2011-06-27
forum: General Help
---

### Post by rcbandit on 2011-06-27
Hi,
   I need to build a custom Ubuntu distribution from the source  code. I'm looking for a custom tool which I can use for automatic  compilation of the packages - for example I put every package source  code into one directory the tool handles the packages and compile them.  Is there such a tool?

Can you guide me how the Ubuntu community compiles the Debian source code?

Regards
Peter

---

### Post by sanderd17 on 2011-06-27
The strength of Ubuntu is just the package management. Packages are pre-compiled programs that install to a certain location together with their dependencies.

If you want to build everything yourself, you cannot use Ubuntu, you need to use something like [http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)

If you just want a custom installation (while still using the ubuntu packages), you can start from the minimal CD, install the packages you want and how you want it. And as a final step use Remastersys to compile your installation to an installable CD.

---

