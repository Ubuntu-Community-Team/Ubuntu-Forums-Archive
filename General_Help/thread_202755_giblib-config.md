---
title: "giblib-config"
date: 2006-06-24
forum: General Help
---

### Post by thunderduck3141 on 2006-06-24
howdey
 i used the guide from 
[http://ubuntuforums.org/showthread.php?t=97199&highlight=e17](http://ubuntuforums.org/showthread.php?t=97199&highlight=e17)
and got a good ways through and then the script spat out 

*** The giblib-config script installed by giblib could not be found
*** If giblib was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GIBLIB_CONFIG environment variable to the
*** full path to giblib-config.
configure: error: Cannot find giblib: Is giblib-config in the path?

anyone have any idea what giblib-config is (I have giblib and giblib-dev installed, both newest versions)

thanks in advance, really want to get e17 working
oh, any beginner's guides to e17, links or something, would also be helkpful (configuring, customizing, not installing)

---

### Post by thunderduck3141 on 2006-06-24
solved it

do

sudo apt-get install giblib-dev pkg-config

then

pkg-config giblib-dev

---

