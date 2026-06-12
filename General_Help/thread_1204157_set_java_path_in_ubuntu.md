---
title: "set java path in ubuntu"
date: 2009-07-04
forum: General Help
---

### Post by asliyanage on 2009-07-04
how to set a java path in ubuntu ?
i installed java using
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-jdk sun-java6-fonts

But i need to know how to set the classpath and path variable in ubuntu?

---

### Post by derekeverett on 2009-07-04
If I remember correctly 

echo $PATH

shows your current path settings

PATH=$PATH:/newpath
updates the path where newpath = absolute path you want to add

or if you are in the directory containing the file you need to add

PATH=.:$PATH

should do the trick - the dot represents the current directory.

---

### Post by Johnny B on 2009-07-04
i set my path in the "~/.profile"
> PATH=;/~/bin;$PATH

[JAVA_HOME, CLASSPATH set up ]("http://ubuntuforums.org/showthread.php?t=217936&highlight=classpath")

---

