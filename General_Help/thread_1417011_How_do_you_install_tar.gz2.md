---
title: "How do you install tar.gz2"
date: 2010-02-26
forum: General Help
---

### Post by JacobVengeance on 2010-02-26
I keep forgetting the command to compile these and install packages, what is the command? Also is there a program that can auto compile these instead of having to open a terminal everytime?

---

### Post by sefs on 2010-02-26
> **JacobVengeance said:**
> I keep forgetting the command to compile these and install packages, what is the command? Also is there a program that can auto compile these instead of having to open a terminal everytime?

I am pretty sure that compression is handled by file-roller which is installed by default in ubuntu.

Look under Accessories -> Archive Manager in your Main menu.

---

### Post by JacobVengeance on 2010-02-26
> **sefs said:**
> I am pretty sure that compression is handled by file-roller which is installed by default in ubuntu.

Look under Accessories -> Archive Manager in your Main menu.

Isn't that to extract it. I need to install it and it came in a tar.gz2 archive.

---

### Post by sandyd on 2010-02-26
what are you installing?

---

### Post by JacobVengeance on 2010-02-26
kthememanager

---

### Post by MisfitI38 on 2010-02-26
tar.gz is simply a combination of compression algorithms. A package with these extensions is typically called a 'tarball'. If the tarball you are referring to is a source package, you can conceivably compile and install it with /usr/bin/make.
First you must extract the tarball with /bin/tar:
```
$ tar -xvf packagename.tar.gz
```
The extracted tarball will generally create a directory named for the package which you will cd to:
```
$ cd packagename
```
There is usually (but not always) a configure script. If you are not familiar with the configure options, run it with the --help switch.
```
$ ./configure --help
```
Compile the source with /usr/bin/make:
```
$ make
```
Install with 
```
# make install
```
glhf :)

---

