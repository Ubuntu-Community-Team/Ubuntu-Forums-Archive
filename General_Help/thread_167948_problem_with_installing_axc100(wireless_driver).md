---
title: "problem with installing axc100(wireless driver)"
date: 2006-04-29
forum: General Help
---

### Post by bbsabc123 on 2006-04-29
Hi everyone..
     I just want to install axc100 to driver my wireless pciid card.  I followed the installing intruduction from [http://acx100.sourceforge.net/wiki/ACX#Installing](http://acx100.sourceforge.net/wiki/ACX#Installing) .
I chose to install outside the kernel tree(in fact, i don't know where the kernel is.) When i typed make -C /lib/modules/`uname -r`/build M=`pwd` . The system show me some directory not find:

jkore@fenner:~$ make -C /lib/modules/`uname -r`/build M=`pwd`
make: *** /lib/modules/2.6.12-9-386/build: There is no such file or directory, stop.

I encounter such no file or directory problem several times. Is that mean our kubuntu directory structure is different from other linux?

Because i am totaly new to kubuntu(or linux), could anyone tell me how to install  axc100. I hope you can put enough detial for me.... THANK YOU SO MUCH~!!

---

