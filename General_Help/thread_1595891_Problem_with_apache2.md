---
title: "Problem with apache2"
date: 2010-10-13
forum: General Help
---

### Post by mprodman on 2010-10-13
I am having a problem with ubuntu remove packages compelety and then re-installing does not help.
 
I installed apache2 with apt-get install apache2  - I messed up some configs so I wanted to remove and reinstall apache. 
 
I removed with apt-get remove apache2  - it still left behind the orignial /etc/apache2 dir so I tired apt-get remove apache2 --purge still left behind traces of apache2 so I just did a rm -rf /etc/apache2 - now when I run apt-get install apache2 it does not create a /etc/apache2 directory and all the files that would normaly be under that directory.

---

### Post by mprodman on 2010-10-13
Nevermind I found that a command that worked 
 
apt-get autoremove apache2 --purge took care of it - once I did the install after that things came back in...

---

