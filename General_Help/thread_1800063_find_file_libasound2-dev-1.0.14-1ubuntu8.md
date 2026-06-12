---
title: "find file libasound2-dev-1.0.14-1ubuntu8"
date: 2011-07-08
forum: General Help
---

### Post by zeelog on 2011-07-08
Synapic tells me I'm supposed to have the file
   libasound2-dev-1.0.14-1ubuntu8   installed,
 but I can't find it anywhere.
 I've checked using find  and  ls -l | grep "libasound2-dev"
 but so far I can not find it anywhere.
 If this is a library, isn't it suppose to be in
 /lib, /usr/lib, or /usr/local/lib ?
  Could anyone tell me in what directory this program may be
and what command I should have used to find it ?
 I'm using Ubuntu 10.10

---

### Post by CatKiller on 2011-07-08
> **zeelog said:**
> Synapic tells me I'm supposed to have the file
   libasound2-dev-1.0.14-1ubuntu8   installed,

Unlikely. That looks much more like a package name than a filename. Viewing the properties of an installed package in Synaptic will tell you the files that it installed.

Perhaps if you said what you were trying to do, someone here could help you to achieve it?

---

### Post by zeelog on 2011-07-09
Thank you Catkiller. By pointing out the obvious, you have
 solved my problem !  I thought I was just looking for
 one library file, like listed in /lib or /usr/lib or /usr/local/lib,
but when a package is installed, in can be a whole lot of files,
like I found out using dpkg -c file_name.deb, none of which 
 have to use the original package name. So I was searching for
 a file name that did not exist.  Problem solved. Thanks!

---

