---
title: "Installing ZoidQuest"
date: 2010-04-22
forum: General Help
---

### Post by xzcallaway on 2010-04-22
I'm trying to install zoidquest.  I've ran ./configure, and then I ran make.  When entering make into the terminal I get the following stuff.

zach@zach-laptop:~/Desktop/zoidsquest-0.0.1$ make
make  all-recursive
make[1]: Entering directory `/home/zach/Desktop/zoidsquest-0.0.1'
Making all in src
make[2]: Entering directory `/home/zach/Desktop/zoidsquest-0.0.1/src'
if g++ -DHAVE_CONFIG_H -I. -I. -I..     -g -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -I/usr/include/libxml2 -MT werror.o -MD -MP -MF ".deps/werror.Tpo" -c -o werror.o werror.cpp; \
	then mv -f ".deps/werror.Tpo" ".deps/werror.Po"; else rm -f ".deps/werror.Tpo"; exit 1; fi
werror.cpp: In member function &#8216;void ErrorLog::DebugMsg(char*)&#8217;:
werror.cpp:33: warning: format not a string literal and no format arguments
werror.cpp: In function &#8216;void CleanExit()&#8217;:
werror.cpp:52: error: &#8216;exit&#8217; was not declared in this scope
make[2]: *** [werror.o] Error 1
make[2]: Leaving directory `/home/zach/Desktop/zoidsquest-0.0.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/zach/Desktop/zoidsquest-0.0.1'
make: *** [all] Error 2


    Ps. you can download a copy of it for your self at: [http://xzcallaway.synthasite.com/problems.php](http://xzcallaway.synthasite.com/problems.php)

---

### Post by SevenMachines on 2010-04-22
hi there, you'll need to include cstdlb to werror.cpp
#include <cstdlib>

---

### Post by xzcallaway on 2010-04-22
That made it work.  Thank you very much.

---

