---
title: "Installing SystemC on ubuntu"
date: 2010-05-15
forum: General Help
---

### Post by DJ_MotionX on 2010-05-15
Hello !!!

I tied to install SystemC ([www.systemc.org](www.systemc.org)) on my ubuntu system yesterday. The tutorial [http://swiss.ubuntuforums.org/showthread.php?p=8976387](http://swiss.ubuntuforums.org/showthread.php?p=8976387) guided me perfect, but i received the same error like the last post of this thread. With the help of google I found this page [http://ubuntuforums.org/showthread.php?t=1431267](http://ubuntuforums.org/showthread.php?t=1431267). But I cannot unserstand the sentence "the trick is to provide an exception to the example folder in the make
file since it is the folder creating the problem". Can anybody tell me what I exactly have to do or how I can provide an exception for the example folder? I am not very familar with make files.

My facts:
Error produced of make:
-----------------------------------------------------------
make[5]: *** [install-data-local] Error 1
make[5]: Leaving directory
`<<home>>/systemc-2.2.0/examples/sysc/fft/fft_flpt'
make[4]: *** [install-am] Error 2
make[4]: Leaving directory
`<<home>>/systemc-2.2.0/examples/sysc/fft/fft_flpt'
make[3]: *** [install-recursive] Error 1
make[3]: Leaving directory `<<home>>/systemc-2.2.0/examples/sysc/fft'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory
`<<home>>/OFFICIAL/systemc-2.2.0/examples/sysc'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `<<home>>/OFFICIAL/systemc-2.2.0/examples'
make: *** [install-recursive] Error 1
----------------------------------------------------------
System: ubuntu 9.04
gcc version: 4.3.3

- Michael

---

### Post by gmargo on 2010-05-15
If you follow the instructions in the INSTALL file, and build within a subdirectory (objdir), then you will not get that "make install" error.  

I compiled, installed, and tested SystemC-2.2.0 on 9.04 Jaunty, and only had to make one minor patch:
```

--- systemc-2.2.0/src/sysc/utils/sc_utils_ids.cpp.00    2006-12-15 12:31:39.000000000 -0800
+++ systemc-2.2.0/src/sysc/utils/sc_utils_ids.cpp       2010-05-15 10:14:40.000000000 -0700
@@ -59,6 +59,8 @@
 //
 
 #include "sysc/utils/sc_report.h"
+#include <cstdlib>
+#include <cstring>
 
 
 namespace sc_core {

```

---

### Post by DJ_MotionX on 2010-05-18
OK Thank you !

With making an objdir Directory the onstallation works perfect.

---

