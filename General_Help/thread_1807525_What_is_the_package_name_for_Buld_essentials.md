---
title: "What is the package name for Buld essentials"
date: 2011-07-19
forum: General Help
---

### Post by flebber on 2011-07-19
I was following a guide to build x264 and tools, it advises to install build-essential. However when i attempted to install build-essntials it said the package doesn't exist.

this is the error.
```
sayth@sayth-TravelMate-5740G:~$ sudo apt-get install build essential
[sudo] password for sayth: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package build is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'build' has no installation candidate
E: Unable to locate package essential
sayth@sayth-TravelMate-5740G:~$ 
```

If I want a build environment how do I do it. I want to build all  the componenets.

---

### Post by Toz on 2011-07-19
It is called **build-essential**.
```
sudo apt-get install build-essential
```

---

### Post by nothingspecial on 2011-07-19
You need the dash build-essential

---

### Post by flebber on 2011-07-19
thanks

---

