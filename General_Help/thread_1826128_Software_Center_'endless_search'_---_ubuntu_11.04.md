---
title: "Software Center 'endless search' --- ubuntu 11.04"
date: 2011-08-16
forum: General Help
---

### Post by netbook_helper on 2011-08-16
Hello, I have been using the software center for a while now, but all of a sudden, everytime a click on a category, ype something in the search category, it just shows the 'searching, spinning line thing' and I dont know what to do!

Anyone have a fix?

Ubuntu 11.04 32 bit
Emachine 350 Netbook

AND TERMINAL SHOWS ME AN ERROR WHEN I TRY TO RUN A SUDO APT-GET!

The install was Super OS, but that should not make a difference.:mad:

---

### Post by netbook_helper on 2011-08-16
How to fix this problem:
1. Open terminal

2. Enter the following commands one by one:
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

3. Done!

---

