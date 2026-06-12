---
title: "Problems installing JRE in 9.10"
date: 2010-10-09
forum: General Help
---

### Post by OxentroT on 2010-10-09
I have tried installing Java runtime environment through Term and it is unsuccessful. An example is as follows:

```
gn0@DaPiLiL:~$ sudo apt-get install sun-java6-plugin
[sudo] password for gn0: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sun-java6-plugin

```

Any suggestions? 
Would be appreciated. 
Thank You

---

### Post by QIII on 2010-10-09
You probably don't have the partner repository activated.

In any case, the version available there is old.  I would uninstall sun-java6 and all of its components, and then follow this method to make sure you have the latest update:

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

Pay attention.  The instructions are slightly different for 32 bit and 64 bit.

---

