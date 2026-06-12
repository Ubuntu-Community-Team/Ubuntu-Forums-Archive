---
title: "setting java classpath has no effect?"
date: 2010-09-10
forum: General Help
---

### Post by Stardom on 2010-09-10
I am trying to install some jar files in a directory and add the directory to the class loader path. In my .bashrc file i have

CLASSPATH="/usr/local/Wolfram/Mathematica/7.0/AddOns/JLink"
export CLASSPATH

however, this has no effect on the classpath! When i do this in clojure

 (println (seq (.getURLs 
(java.lang.ClassLoader/getSystemClassLoader)))) 


i do not get the above path. How do i add to the class loader path?

---

### Post by Stardom on 2010-09-12
woops, i had already supplied the classpath when starting java in emacs

---

### Post by priyaurs on 2011-10-10
how to add jar files to class path? can any1 pls tel me d command

---

