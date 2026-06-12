---
title: "Installing Cray LC under Ubuntu"
date: 2010-08-03
forum: General Help
---

### Post by jeffe23 on 2010-08-03
I previously had Cray LC running under Redhat Linux from 2003.  Recently I bought an HPZ800 workstation and installed Ubuntu-64 so that I can get to all of the memory (12Gbytes).  I needed to install lesstif but was really struggling so instead I installed geomview which comes with lesstif using sudo apt-get install gemview.  Geomview works great and lesstif is installed!
 
Now I am struggling getting LC to work.  In the past under Redhat this was easy.  Just download from Cray:
 
[http://lc.cray.com](http://lc.cray.com)
 
gunzip, cd to that directory, type ./lc and voila!
 
Under Ubuntu, all I get is bash: ./lc:  No such file or directory
 
I tried moving it to /usr/local/bin with sudo su mv ./lc /usr/local/bin
 
when I type lc I get bash: /usr/local/bin/lc : No such file or directory
 
Why doesn't this work?  The file is clearly there but Ubuntu doesn't see it?
 
Thanks for any help

---

