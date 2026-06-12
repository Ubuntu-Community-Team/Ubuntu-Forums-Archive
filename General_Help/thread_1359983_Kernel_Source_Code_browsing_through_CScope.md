---
title: "Kernel Source Code browsing through CScope"
date: 2009-12-20
forum: General Help
---

### Post by GeorgeOfTheBush on 2009-12-20
I need to setup cscope for browsing the linux kernel source code. 

The link [http://cscope.sourceforge.net/large_projects.html](http://cscope.sourceforge.net/large_projects.html) says that the kernel source code needs to be downloaded from kernel.org.

I have Ubuntu 9.10 installed thru wubi. **Doesn't that mean I already have the kernel source code? **Please clarify.

---

### Post by pbrane on 2009-12-20
Not unless you installed the source itself. You should be able to install it by typing this in a terminal.
```

sudo apt-get install linux-source

```

---

### Post by GeorgeOfTheBush on 2009-12-20
/usr/src on my system shows the following directories.

```

georgeofthebush@ubuntu:~$ ls -l /usr/src/
total 16
drwxr-xr-x 23 root root 4096 2009-10-29 02:36 linux-headers-2.6.31-14
drwxr-xr-x  7 root root 4096 2009-10-29 02:36 linux-headers-2.6.31-14-generic
drwxr-xr-x 23 root root 4096 2009-12-19 13:12 linux-headers-2.6.31-16
drwxr-xr-x  7 root root 4096 2009-12-19 13:12 linux-headers-2.6.31-16-generic

```**What do these directories linux-headers-* refer to? Linux kernel source code or something else?**

I am new to the linux kernel. Hence, please clarify. Thanks.

---

### Post by pbrane on 2009-12-20
The linux headers are the header files needed to compile other source code against the kernel. For instance to build a kernel driver. The actual kernel source is not needed. If you want to study the kernel itself you will have to have a copy of the source. You can get that by running the command I posted earlier.

---

