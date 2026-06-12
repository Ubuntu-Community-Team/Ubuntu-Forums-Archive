---
title: "How To Create Deb Package"
date: 2010-02-22
forum: General Help
---

### Post by dani_b1 on 2010-02-22
Hi
I would like to create deb package (Consist  kernel driver, binary file )
using the command fakeroot dpkg-deb --build 
To test the package i use lintian 
1. the moudle i need to put in /lib/modules/...
2. the binary file in usr/local/bin
I create a directory called debian and create all the directory (/lib/modules/... ' /usr/local/bin')
the package is created and when i use the litian command i get these errors
dir-or-file-in-local.
When i tried to put the binary in /tmp and then use the postinst script to copy it to /usr/local/bin i get the error dir-or-file-in-tmp
How can i solve this problem?

---

