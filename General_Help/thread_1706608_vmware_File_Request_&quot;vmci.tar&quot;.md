---
title: "vmware File Request &quot;vmci.tar&quot;"
date: 2011-03-14
forum: General Help
---

### Post by highspider on 2011-03-14
First off this for x86 with Kernel 2.6.35-27  
  I Don't think it makes a hoot what vmware your using you some how patched or got 
  It working under Kernel 2.6.35-27
                 -or-    Kernel 2.6.35-27-generic 
                 -or-    Kernel 2.6.35-27-generic-pae

file would be here 
/usr/lib/vmware/modules/source/vmci.tar 

I've tried patching aka adding the missing pre-pross directive header file 
#include "compat_sched.h"

I can't get the VMCI sockets to work. Got everything else working.

This file is free with VMware Player which is also free Im not hornswoggling or bamboozling here I just can't make work with Ubuntu.

and yes I tried [http://ubuntuforums.org/showthread.php?t=1596105&highlight=vmci.tar&page=2](http://ubuntuforums.org/showthread.php?t=1596105&highlight=vmci.tar&page=2)  no good  

also Im using VMware-Player-2.5.5-328052.i386.bundle
   but file should be universal since its for a "kernel module"

---

### Post by highspider on 2011-03-16
I removed vmware and went with virtual box

[http://mesbalivernes.blogspot.com/2008/01/virtual-box-booting-from-existing.html](http://mesbalivernes.blogspot.com/2008/01/virtual-box-booting-from-existing.html)

I was able to virtual box my existing windows partition with out having to copy it to iso or any thing weird.

I think virtual box is a better program with less issues this solved my problem.

---

