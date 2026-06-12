---
title: "debootstrap: Failure trying to run: chroot &lt;path&gt; mount -t proc proc /proc"
date: 2011-01-22
forum: General Help
---

### Post by tranduyhung on 2011-01-22
Hi, when I run debootstrap I get the following result:

```
sudo debootstrap --arch=i386 maverick chroot/
I: Retrieving Release
I: Retrieving Packages
I: Validating Packages
I: Resolving dependencies of required packages...
I: Resolving dependencies of base packages...
I: Checking component main on http://archive.ubuntu.com/ubuntu...
I: Retrieving adduser
I: Validating adduser
I: Retrieving apt
...(more here)...
I: Extracting udev...
I: Extracting upstart...
I: Extracting util-linux...
I: Extracting xz-utils...
I: Extracting zlib1g...
**W: Failure trying to run: chroot /home/user/test/chroot mount -t proc proc /proc**
```

My debootstrap version is 1.0.23ubuntu1. I use Ubuntu Maverick.

How could I fix this problem? Thanks!

---

### Post by tranduyhung on 2011-02-19
Anyone :( ?

---

### Post by Joshua on 2011-11-03
I'm not sure if this is applicable, but my <path> had a space in a directory name that prevented it from running.

One directory was called "AWS Workspace" and after I changed it to "AWS_Workspace" the process appeared to continue on with the installation properly.

Again, I'm not sure if this is applicable since your path, "/home/user/test/chroot" doesn't appear to have any spaces.  But I thought there was a possibility that you were just using a generic path in your post.

---

### Post by mercvrivs on 2012-04-05
Use --verbose and --foreign

> debootstrap --verbose --foreign ....etc

It worked for me...

---

