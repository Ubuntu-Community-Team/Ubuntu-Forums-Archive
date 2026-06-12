---
title: "FlightGear OSG compilation error"
date: 2011-06-09
forum: General Help
---

### Post by hihihi100 on 2011-06-09
No rule to make target `/usr/lib/libm.so', needed by `lib/libosg.so.2.9.16'

Thars  what I get after, in my ubuntu 11.04, FGFS brisa script (GIT) after  trying to sh download_and_compile.sh OSG UPDATE, The relevant lines so  far are:

[  0%] Built target OpenThreads
make[2]: *** No rule to make target `/usr/lib/libm.so', needed by `lib/libosg.so.2.9.16'.  Stop.
make[1]: *** [src/osg/CMakeFiles/osg.dir/all] Error 2
make: *** [all] Error 2
[  0%] Built target OpenThreads
make[2]: *** No rule to make target `/usr/lib/libm.so', needed by `lib/libosg.so.2.9.16'.  Stop.
make[1]: *** [src/osg/CMakeFiles/osg.dir/all] Error 2
make: *** [all] Error 2
/usr/share/games/FlightGear

I  havent had problems pulling git to my data folder, or with sh  download_and_compile.sh FGFS UPDATE, sh download_and_compile.sh PLIB  UPDATE, sh download_and_compile.sh FGRUN UPDATE...

help please

Can it be related to permission issues? I recently changed my username

---

