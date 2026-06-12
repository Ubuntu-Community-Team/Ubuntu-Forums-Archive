---
title: "How to enable java?"
date: 2010-10-28
forum: General Help
---

### Post by thairsadi77 on 2010-10-28
I am new to linux i general.I have just installed ubuntu 10.10 and it is amazing
the only problem is that I cant use java 
I installed java runtime 6 update 22 properly I guess but still when i go to any website running java like for e.g. yahoo card games ,it says no java enabled
I tried that in the terminal
```
sudo update-alternatives --config java
```
but I got this result
```
There is only one alternative in link group java: /usr/lib/jvm/java-6-sun/jre/bin/java
Nothing to configure
```
plz help me 
I dont want to use windows anymore

---

### Post by GregBrannon on 2010-10-28
Try this guide:

[Maverick Java Install]("http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html")

You may need to focus on installing the plug-in for your browser, but you didn't mention which one you were using.

---

### Post by gandaran on 2010-10-28
sun-java is in the archive.canonical partner repository, just enable the repo in software sources and update the package list then you can install the sun-java6-plugin.
remove all the openjdk-java packages or just the  java  'icedtea-plugin' if you have any dependent openjdk packages.
no need to configure java if you remove the icedtea-plugin.

update,
if you already have sun-java installed and not openjdk-java then you are just missing the plugin, install command
```
sudo apt-get install sun-java6-plugin
```

---

### Post by gandaran on 2010-10-28
> **GregBrannon said:**
> Try this guide:

[Maverick Java Install]("http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html")

You may need to focus on installing the plug-in for your browser, but you didn't mention which one you were using.
this guide is incorrect! sun java is in the archive.canonical repository not multiverse repository !

---

### Post by thairsadi77 on 2010-10-28
> **gandaran said:**
> sun-java is in the archive.canonical partner repository, just enable the repo in software sources and update the package list then you can install the sun-java6-plugin.
remove all the openjdk-java packages or just the  java  'icedtea-plugin' if you have any dependent openjdk packages.
no need to configure java if you remove the icedtea-plugin.

update,
if you already have sun-java installed and not openjdk-java then you are just missing the plugin, install command
```
sudo apt-get install sun-java6-plugin
```
tyvm now it works

---

