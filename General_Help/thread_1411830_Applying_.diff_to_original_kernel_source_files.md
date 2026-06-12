---
title: "Applying .diff to original kernel source files"
date: 2010-02-20
forum: General Help
---

### Post by lotuseclat79 on 2010-02-20
Hi,

I have downloaded (I did not use git, but apt-get source command to download the files) the following source/diff files for Ubuntu Linux kernel version 2.6.31-19.56 (Synaptic Package Manager says w/all Ubuntu Patches):
linux_2.6.31.orig.tar.gz and 
linux_2.6.31-19.56.diff.gz


I have installed the source in a fake chroot/usr/src directory on hard disk with enough free space, and the required kernel compilation tools, but I am fairly certain that the diff probably needs to be applied to the original source based on their sizes and dates:
-rw-r--r-- 1 root root  12238431 2010-02-04 01:05 linux_2.6.31-19.56.diff
-rw-r--r-- 1 root root 365711360 2009-09-16 02:04 linux_2.6.31.orig.tar

I would guess by the dates of the above two files the tar file is the original source, and the diff file is the difference between the original release on 2009-09-16 and 2010-02-04.

What is(are) the command(s)/arguments to apply the .diff file (patch) to the original sources to insure that the source I would be compiling has all of the most current patches applied to it for version 2.6.31-19.56? 

Tia,

-- Tom

---

