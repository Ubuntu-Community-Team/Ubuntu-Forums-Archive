---
title: "JRE - Java Runtime"
date: 2006-02-13
forum: General Help
---

### Post by jansenh on 2006-02-13
Hi forum.

I am new to ubuntu [5.10, Gnome 2.12.1]; having trouble with JRE. My Firefox 1.0.7 cannot launch Java content. And it wont install JRE automagically... :confused: 

I have downloaded/installed jre-1_5_0_06-linux-i586.bin from Sun, but I cannot see how to install it as a plugin in Firefox, neither do I know how to tell the OS itself where to find the new JRE.

Anyone?

---

### Post by Perfect Storm on 2006-02-13
```
sudo gedit /etc/apt/sources.list 
```

add:

[b]## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free[/b]

then:

```
sudo apt-get update
sudo apt-get install sun-j2re1.5

```

---

### Post by jansenh on 2006-02-13
Thanx! It works just great now. :)

---

### Post by draven on 2006-02-13
And for us AMD 64bit guys? Let me guess, 32bit chroot?

---

### Post by SWAT on 2006-02-13
[QUOTE=jansenh]Hi forum.

I am new to ubuntu [5.10, Gnome 2.12.1]; having trouble with JRE. My Firefox 1.0.7 cannot launch Java content. And it wont install JRE automagically... :confused: 

I have downloaded/installed jre-1_5_0_06-linux-i586.bin from Sun, but I cannot see how to install it as a plugin in Firefox, neither do I know how to tell the OS itself where to find the new JRE.

Anyone?[/QUOTE]Ahum, if you really want to install the Java from the website, you can. You just have a FireFox linkage problem. Look at the [second part of my HowTo](http://www.zwhlug.nl/content/java_how_to_install_the_sun_java_sdk_jre_1_5_0_incl_firefox_configuation) for the FireFox configuration.

---

