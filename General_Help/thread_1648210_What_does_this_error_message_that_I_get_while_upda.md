---
title: "What does this error message that I get while updating mean?"
date: 2010-12-18
forum: General Help
---

### Post by metalf8801 on 2010-12-18
I'm running Ubuntu 10.10 and I cannot install any updates or new programs using the update manger, Synaptic, Ubuntu Software Center, apt-get, or aptitude. 

Using Synaptic I unchecked all of the updates except for gbrainy and this is the error message I get  

E: /var/cache/apt/archives/gbrainy_1.60-1~getdeb1_all.deb: subprocess dpkg-deb --control returned error exit status 2

What does "error exit status 2" mean and where can I find more information about error messages? I've been googling trying to find a list of the what different exist statues and what they mean but so far I haven't found anything. Does anyone know of any good documentation on different error messages? 


I just found this under Details 
tar: Skipping to next header
tar: Exiting with failure status due to previous errors
dpkg-deb: subprocess tar returned error exit status 2
dpkg: error processing /var/cache/apt/archives/gbrainy_1.60-1~getdeb1_all.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/gbrainy_1.60-1~getdeb1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

Thank you 
Dan

---

### Post by surfer on 2010-12-18
does
```
$ sudo apt-get install --reinstall gbrainy
```
work?

maybe run
```
$ sudo apt-get clean
```
first.

---

### Post by metalf8801 on 2010-12-18
I know what was causing the problem but I'm mainly trying to figure out what "error code (1)" and "error exit status 2" mean. 

I had installed ESET NOD32 Antivirus 4 for Linux Desktop Beta just before this started and I just uninstalled it and now I can installed updates.

---

