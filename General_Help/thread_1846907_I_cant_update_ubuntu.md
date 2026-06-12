---
title: "I cant update ubuntu?"
date: 2011-09-19
forum: General Help
---

### Post by shresthanator on 2011-09-19
I cant seem to update ubuntu (had this problem for like a couple weeks now). Whenever I hit update...I get this error message: 


Failed to fetch [http://ppa.launchpad.net/cheleb/blender-svn/ubuntu/pool/main/b/blender/blender_2.59.2+svn40305~natty1_i386.deb](http://ppa.launchpad.net/cheleb/blender-svn/ubuntu/pool/main/b/blender/blender_2.59.2+svn40305~natty1_i386.deb) 404  Not Found


...so I can tell it has to do with blender...but this is preventing me from updating anything else...I think I have two versions of blender on my computer (one that I just installed with the software manager) and another version (2.59) that I just have on the computer.

---

### Post by drs305 on 2011-09-19
Disable this ppa in your sources. Open Software Sources as root:
```
gksu software-properties-gtk
```

Go to the 'Other Software' tab and locate the cheleb PPA.
Untick it, then Close.

Update the repository list as you normally do and ensure you no longer have the error.

---

### Post by wildmanne39 on 2011-09-19
Hi, that ppa is not there anymore either the server is down or it has been removed, so open synaptic and click on settings, repositories, other software and uncheck it or delete it.
Thank you

---

