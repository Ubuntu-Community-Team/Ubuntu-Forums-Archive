---
title: "Problems installing NetCDF 4.1.2"
date: 2011-06-14
forum: General Help
---

### Post by ikirby77 on 2011-06-14
Hi All,
 
I am having problems installing NetCDF 4.1.2. on Ubuntu, everytime I go to configure the program it comes up with the message:
 
configure: error: cannot locate neither curl-config or a curl directory
 
I am trying to install NetCDF 4.1.2 using g95 fortran on the linux operating system Ubuntu. I would be very grateful if anyone could tell me why this error is appearing and how I may get round this problem.
 
Thanks 
 
Ian

---

### Post by apmcd47 on 2011-06-14
It sounds like they are expecting curl to be installed. You should be able to get curl by typing:```
sudo apt-get install curl
``` into a command prompt or using your favourite GUI package manager. You should also check the README and INSTALL files for other prerequisites.

Andrew

---

