---
title: "command source codes?"
date: 2009-09-22
forum: General Help
---

### Post by abhilashm86 on 2009-09-22
well after many days, i want to now view and understand logic and tweak some commands in ubuntu:)
i see only binary files in /usr/bin......
when i use WHEREIS command to see commands, i see only manpages and binary,
how to see and edit commands source code, any tutorials or how to do it?
i've played with mutt, grub, fstab others, but i want to view commands source code.........

---

### Post by P4man on 2009-09-22
```
apt-get source nameofpackage
```

assuming you have the correct source repo's in your sources.list, that will fetch the sourcecode for any given package.

---

### Post by abhilashm86 on 2009-09-22
> **P4man said:**
> ```
apt-get source nameofpackage
```

assuming you have the correct source repo's in your sources.list, that will fetch the sourcecode for any given package.

abhilash@abhilash:~$ sudo apt-get source whereis
[sudo] password for abhilash: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for whereis

which deb url i need to include in sources.lst to correct this error?

---

### Post by P4man on 2009-09-22
whereis is not a package. Its part of a bigger package (util-linux).
To find out which one, you can use this:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
(scroll down to "Search the contents of packages" )

---

### Post by amauk on 2009-09-22
> **P4man said:**
> whereis is not a package. Its part of a bigger package (util-linux).
To find out which one, you can use this:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
(scroll down to "Search the contents of packages" )You can also do this on the command line

```
dpkg -S /usr/bin/whereis
```

---

### Post by abhilashm86 on 2009-09-22
> **amauk said:**
> You can also do this on the command line

```
dpkg -S /usr/bin/whereis
```

yes i get this output at terminal, where is the source code of whereis now? please tell in detail?
```
abhilash@abhilash:~$ dpkg -S /usr/bin/whereis
util-linux: /usr/bin/whereis

```

---

### Post by P4man on 2009-09-22
dpkg -S will only show you which package to download. To get the source code of "whereis", you still need to download the source of the entire util-linux package

```
sudo apt-get source util-linux
```

Then it will be downloaded and extracted to your homefolder. In this case, to ~/util-linux-2.16. "whereis.c" is in misc-utils subfolder.

---

### Post by amauk on 2009-09-22
also, if you're planning on compiling stuff, make sure you have all the build dependencies

```
sudo apt-get build-dep util-linux
```

This will pull in all the stuff required to compile util-linux

from the apt-get man page
> build-dep causes apt-get to install/remove packages in an attempt to satisfy the build dependencies for a source package.

---

### Post by geirha on 2009-09-22
You do not need to run apt-get source as root (with sudo) btw, and if you don't need to, you shouldn't (in fact, you won't be able to build the source as your user since the source tree will be owned by root). I think people are getting a bit too trigger-happy with that sudo nowadays.

---

### Post by P4man on 2009-09-22
good point. I guess "apt-get" automatically triggers my fingers to type "sudo" :)

---

### Post by abhilashm86 on 2009-09-22
> **P4man said:**
> good point. I guess "apt-get" automatically triggers my fingers to type "sudo" :)

+1, in ubuntu, when i see apt-get, i tend to use sudo, now after you people telling, i need to think and do things!! 
i messed up mutt and also eclipse-FLEX plugin as sudo and need to use those as root login!! thats bizzare:(

---

