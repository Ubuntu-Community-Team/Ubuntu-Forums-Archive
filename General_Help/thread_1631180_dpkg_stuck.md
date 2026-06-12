---
title: "dpkg stuck"
date: 2010-11-26
forum: General Help
---

### Post by igascream on 2010-11-26
Have a problem with dpkg. It stuck when trying to install a package ,at Unpacking replacement , getting no errors .
last things from dpkg.log before it stops:
      
      > 
startup archives unpack
upgrade dpkg 1.15.8.4ubuntu3 1.15.8.4ubuntu3
      status half-installed dpkg 1.15.8.4ubuntu3
      status triggers-pending man-db 2.5.7-4
      status half-installed dpkg 1.15.8.4ubuntu3

---

### Post by dino99 on 2010-11-26
dpkg is a critical package, take care 

what have you done to get this issue and how ? (apt-get, synaptic, ...)

sudo apt-get update
sudo apt-get install -f

---

### Post by igascream on 2010-11-26
Already tried everything ... it broke first at chromium update I thought it's chromium problem ,but then tried to install other packages ,getting the same problem. altitude ,apt-get work normally until the install the package and use dpkg then I get a problem.

---

### Post by dino99 on 2010-11-26
follow this thread WITH your dpkg package version of course (1.15.8.4ubuntu3 ):

[http://ubuntuforums.org/showpost.php?p=9500205&postcount=5](http://ubuntuforums.org/showpost.php?p=9500205&postcount=5)

---

### Post by igascream on 2010-11-26
Helped ,Thanks

---

