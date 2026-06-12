---
title: "Cannot find lguest tools"
date: 2012-05-04
forum: General Help
---

### Post by kiminaiseah on 2012-05-04
hi ,

im struggling with compiling a kernel 3.4 

when executing 

> make-kpkg --initrd --initrd

it giving me at last line 

> debian/ruleset/targets/common.mk:286: *** Cannot find lguest tools.  Stop.

below are full debug 

> [http://pastebin.com/jy2GSiN3](http://pastebin.com/jy2GSiN3)

---

### Post by kiminaiseah on 2012-05-04
already solved @ forums.debian.net

i done with 

make menuconfig

processor type and features > paravirtualized guest support > lguest guest support (uncheck)

---

