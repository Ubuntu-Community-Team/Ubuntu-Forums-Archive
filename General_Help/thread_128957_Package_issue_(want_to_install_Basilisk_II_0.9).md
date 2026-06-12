---
title: "Package issue (want to install Basilisk II 0.9)"
date: 2006-02-12
forum: General Help
---

### Post by jonathanhayward on 2006-02-12
When I try to download the Ubuntu passage from: 

[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmultiverse%2Fb%2Fbasilisk2%2Fbasilisk2_0.9.20050730-1_i386.deb&md5sum=e575e25ed1eb7719c580bd94df11180d&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmultiverse%2Fb%2Fbasilisk2%2Fbasilisk2_0.9.20050730-1_i386.deb&md5sum=e575e25ed1eb7719c580bd94df11180d&arch=i386&type=main)

I get:

root@inner-sanctum:~/download# dpkg -i basilisk2_0.9.20050730-1_i386.deb
Selecting previously deselected package basilisk2.
(Reading database ... 103904 files and directories currently installed.)
Unpacking basilisk2 (from basilisk2_0.9.20050730-1_i386.deb) ...
dpkg: dependency problems prevent configuration of basilisk2:
 basilisk2 depends on libgcc1(>= 1:4.0.2); however:
  Version of libgcc1 on system is 1:4.0.1-4ubuntu9.
 basilisk2 depends on libstdc++6 (>= 4.0.2-3); however:
  Version of libstdc++6 on system is 4.0.1-4ubuntu9.
dpkg: error processing basilisk2 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 basilisk2

How do I upgrade libgcc1 and libstdc++6? I tried running (history:)

  501  apt-get upgrade libgcc1
  502  apt-get -f upgrade libgcc1
  503  apt-get upgrade libstdc++6
  504  apt-get -f upgrade libstdc++6
  505  apt-get -f install libstdc++6

However, these didn't upgrade the library. How do either download a version of Basilisk II that will run under the installed libraries (1:4.0.1-4ubuntu9 and 4.0.1-4ubuntu9), or set things up so the version I downloaded will work?

---

