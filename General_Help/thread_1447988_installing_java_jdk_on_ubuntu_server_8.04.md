---
title: "installing java jdk on ubuntu server 8.04"
date: 2010-04-06
forum: General Help
---

### Post by karl2010 on 2010-04-06
The log.

```
root@s:/home/karl# apt-get install openjdk-6-jre-headless
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  openjdk-6-jre-headless: Depends: ca-certificates but it is not installable
                          Depends: java-common (>= 0.28) but it is not installable
                          Depends: libaccess-bridge-java (>= 1.22) but it is not installable
                          Depends: libfreetype6 (>= 2.3.5) but it is not going to be installed
                          Depends: liblcms1 but it is not going to be installed
                          Depends: openjdk-6-jre-lib (>= 6b11-2ubuntu2.1) but it is not going to be installed
                          Depends: rhino but it is not installable
  webmin: Depends: libnet-ssleay-perl but it is not installable
          Depends: openssl but it is not going to be installed
          Depends: libauthen-pam-perl but it is not installable
          Depends: libio-pty-perl but it is not installable
          Depends: libmd5-perl but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@s:/home/karl#

```

If anyone can help me with this i will be forever grateful

---

### Post by ubun2warrior on 2010-04-06
you can install jdk from synaptics very easily. Just type jdk in the search box and you can do the installation. Its very simple.

---

### Post by ajgreeny on 2010-04-06
It should be very straightforward the way you tried.

Assuming the server is without a GUI, make sure your repositories are updated with sudo apt-get update, then try installing again.  You could also try the sun-java version of jdk, instead of the open version.

---

### Post by karl2010 on 2010-04-06
Thanks Guys/Girls i finally got it.

---

### Post by ajgreeny on 2010-04-06
Just out of interest; how?

---

