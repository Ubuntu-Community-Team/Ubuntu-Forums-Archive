---
title: "how to uninstall soft and application"
date: 2012-02-07
forum: General Help
---

### Post by warrior_king on 2012-02-07
I want know how will do uninstall lamp-server or other soft and application ?

---

### Post by HiImTye on 2012-02-07
for most programs you can remove them using the ubuntu software center. for specific packages, you might need to use synaptic (or if you know the package name, apt-get)

do add synaptic (if you don't already have it)
```
sudo apt-get install synaptic
```synaptic is pretty easy to figure out, you type in the search box and right click, choose remove, click apply.

software center is pretty easy too. you type in the search box, select it, click 'remove'

aptitude/apt-get can get more complex but are powerful tools once you are used to the command line
to find something using aptitude
```
aptitude search <package>
```and to subsequently install whatever you find
```
sudo apt-get install <package>
```and to remove that package
```
sudo apt-get remove <package>
```if you don't have aptitude
```
sudo apt-get install aptitude
```

---

