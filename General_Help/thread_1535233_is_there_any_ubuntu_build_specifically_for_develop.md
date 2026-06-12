---
title: "is there any ubuntu build specifically for developers"
date: 2010-07-20
forum: General Help
---

### Post by rajeevisonline on 2010-07-20
I mainly do c/c++ development in linux...also i sometimes use java and i would really like it if i had mono also.. so i am pretty much looking for support for all major languages with ides...can u suggest me a distribution?

---

### Post by valbaca on 2010-07-20
Linux itself is whatever you want to make it into. Creating a developer workstation is one of the easiest.
 
build-essential is the minimum to begin developing. It includes gcc, g++,dpkg-dev,libc-dev, and make.
```
sudo apt-get install build-essential
```
 
If you're going for an IDE that can work with C++ and Java, I suggest eclipse:
```
sudo apt-get install eclipse
```
 
**EDIT: I just wanted to add that Eclipse IDE supports much more than just Java and C++. Netbeans is also similar. You'll have to decide for yourself which you prefer.**

---

