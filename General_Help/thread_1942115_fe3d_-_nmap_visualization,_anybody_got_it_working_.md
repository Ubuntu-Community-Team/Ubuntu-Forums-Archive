---
title: "fe3d - nmap visualization, anybody got it working on Ubuntu?"
date: 2012-03-16
forum: General Help
---

### Post by ingramproductions on 2012-03-16
[fe3d]("http://projects.icapsid.net/fe3d/") - They provide instructions for compiling it in Fedora [here]("http://projects.icapsid.net/fe3d/wiki/Building"), but i'm not an expert on building software. When I try to follow them (i substitute the commands for Fedora with Ubuntu equivalent), I get this error when running the **make** command:
```
make
 cd .. && /bin/bash /home/user/Downloads/fe3d_0.11.2/build/test/fe3d/missing --run automake-1.10 --gnu 
cd .. && /bin/bash /home/user/Downloads/fe3d_0.11.2/build/test/fe3d/missing --run autoconf
Making all in src
make[1]: Entering directory `/home/user/Downloads/fe3d_0.11.2/build/test/fe3d/build/src'
make[2]: Entering directory `/home/user/Downloads/fe3d_0.11.2/build/test/fe3d/build'
 cd .. && /bin/bash /home/user/Downloads/fe3d_0.11.2/build/test/fe3d/missing --run automake-1.10 --gnu 
cd .. && /bin/bash /home/user/Downloads/fe3d_0.11.2/build/test/fe3d/missing --run autoconf
make[2]: Leaving directory `/home/user/Downloads/fe3d_0.11.2/build/test/fe3d/build'
cd .. && make  am--refresh
make[2]: Entering directory `/home/user/Downloads/fe3d_0.11.2/build/test/fe3d/build'
 cd .. && /bin/bash /home/user/Downloads/fe3d_0.11.2/build/test/fe3d/missing --run automake-1.10 --gnu 
cd .. && /bin/bash /home/user/Downloads/fe3d_0.11.2/build/test/fe3d/missing --run autoconf
make[2]: Leaving directory `/home/user/Downloads/fe3d_0.11.2/build/test/fe3d/build'
g++ -DHAVE_CONFIG_H -I. -I../src/include -I../../src -I../../include -I../../src/include -DFE_DATA_DIR="\"/usr/local/share/fe3d/\"" -I/usr/lib/wx/include/gtk2-unicode-release-2.8 -I/usr/include/wx-2.8 -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -D__WXGTK__  -g -O2  -MT fe3d-fe_config.o -MD -MP -MF .deps/fe3d-fe_config.Tpo -c -o fe3d-fe_config.o `test -f 'fe_config.cpp' || echo '../../src/'`fe_config.cpp
In file included from /usr/include/wx-2.8/wx/glcanvas.h:54,
                 from ../../src/include/fe_include.hpp:53,
                 from ../../src/fe_config.cpp:21:
[B]/usr/include/wx-2.8/wx/gtk/glcanvas.h:19: fatal error: GL/gl.h: No such file or directory
compilation terminated.[/B]
make[1]: *** [fe3d-fe_config.o] Error 1
make[1]: Leaving directory `/home/user/Downloads/fe3d_0.11.2/build/test/fe3d/build/src'
make: *** [all-recursive] Error 1
```
Has anybody got this working on Ubuntu before? what do I need to do? I'm using Ubuntu 10.10 32 bit

Thanks

---

