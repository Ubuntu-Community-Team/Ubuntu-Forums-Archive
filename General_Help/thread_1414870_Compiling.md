---
title: "Compiling"
date: 2010-02-24
forum: General Help
---

### Post by bullu on 2010-02-24
Hi I am quite new in Linux overall....I have been using Ubuntu 9.10 Karmic for abt 3 months now....
I wanted to know how do i complie tar.gz files .
Step by step instructions would be very much helpful....

---

### Post by karthick87 on 2010-02-24
Install build-essentials from terminal..**sudo apt-get install build-essential**

---

### Post by lisati on 2010-02-24
You need to extract the files first, much like you would extract a zip file. There's often a "readme" file included.

---

### Post by darolu on 2010-02-24
Step by step would be:
1. Extract the files from your .tar.gz (tar.gz is like .zip or .rar files)
2. Install all the dependencies that you don't meet. You can find a list of dependencies on the site where you downloaded the source code or reading the "readme/installation" file.
3. Configure and Compile.
4. Install.

How to do this depends on the program you want to compile; installing the package getyourkarthick told you, installs the more popular developing tools (including gcc [a compiler] and make) you do want to install it; I'd recommend installing automake and cmake too.

Anyways, you need to read the "readme" file or installation instructions in your program's website to know what steps to follow; in most cases this is what you need to do to compile and install:
```
$ cd /your/source
$ ./configure
$ make
$ make install
```
Use of sudo may be needed. Always refer to your program's documentation.

---

### Post by steviefordi on 2010-02-24
You can start here:
[https://help.ubuntu.com/community/CompilingEasyHowTo]("https://help.ubuntu.com/community/CompilingEasyHowTo")

And also read this:
[https://help.ubuntu.com/community/CompilingSoftware]("https://help.ubuntu.com/community/CompilingSoftware")

It was with the help from these two documents that I learned what to do myself!

---

