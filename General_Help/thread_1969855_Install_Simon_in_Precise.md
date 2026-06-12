---
title: "Install Simon in Precise?"
date: 2012-04-30
forum: General Help
---

### Post by Orcris on 2012-04-30
How do I install Simon Listens speech recognition on Precise? I can't find any instructions.

---

### Post by scotty64 on 2012-08-09
There is a new PPA that includes a Precise build:
[https://launchpad.net/~simon-listens/+archive/releases](https://launchpad.net/~simon-listens/+archive/releases)

---

### Post by johnaaronrose on 2012-12-14
It's a mystery as to the details to be used in the add-apt-repository command. I expect it might be ppa:simon/simonteam. Waiting for answer from simonteam's admin.

---

### Post by johnaaronrose on 2012-12-14
It's 
ppa:simon-listens/releases

---

### Post by r3xu5 on 2013-03-08
Hi everyone/anyone, I've recently migrated from ubuntu to kubuntu precise. Main reason being that after many fails trying to build simon listens 
version 0.4.0 on gnome, I thought it would be simpler on kde. :roll: I get the 0.3.0 version working ok but after days of trying I just cant get the new version to build. ](*,)  I've got all the dependencies built (i think), I get this error at 21% of build when running the build_ubuntu.sh:

simon-0.4.0/build/simonlib/simonvision/../../../simonlib/simonvision/imageanalyzer.h:22:16: fatal error: cv.h: No such file or directory
compilation terminated.
make[2]: *** [simonlib/simonvision/CMakeFiles/simonvision.dir/simonvision_automoc.cpp.o] Error 1
make[1]: *** [simonlib/simonvision/CMakeFiles/simonvision.dir/all] Error 2
make: *** [all] Error 2

cant find any documentation on this problem, please help!!!!
greatful for any assistance

---

### Post by morsedl on 2013-05-30
This is probably too late in coming, but for what it's worth:

The problem seems to reside in changes made in opencv, specifically, a new source file structure for opencv2.

I just finished building simon from source on Ubuntu 12.04 LTS (64-bit) and so far it's working fine (at least it runs, I've not real trained it or used it yet).

 I found that the following three substitions, which must be made in numerous simon files (i.e., just keep running "make" in the build directory, wait for an error, and edit the problematic file) -- enabled me to build  simon from the source code just fine:

```

/* #include "cv.h" */
#include <opencv2/opencv.hpp>
/* #include <highgui.h> */
#include <opencv2/highgui/highgui_c.h>
/* include <cxcore.h> */
#include <opencv2/core/core_c.h>

```

In other words, all references to #include <cv.h> (or "cv.h") become #include <opencv2/opencv.hpp>, all references to #include <highgui.h> (or "highgui.h") become #include <opencv2/highgui/highgui_c.h>, and all references to #include <cxcore.h> (or cxcore.h) become #include <opencv2/core/core_c.h>.  Of course, not every source file that leads to a compiler error such as these includes all three of these include files; indeed, most just require 1 or 2 substitutions.  It's tedious but simple enough to make these corrections.

I trust that you know that the text between /* and */ in the code above are simply comments (i.e., I have commented out the old, incorrect code and put the correct code immediately on the next line).

Hope this helps.


> **r3xu5 said:**
> Hi everyone/anyone, I've recently migrated from ubuntu to kubuntu precise. Main reason being that after many fails trying to build simon listens 
version 0.4.0 on gnome, I thought it would be simpler on kde. :roll: I get the 0.3.0 version working ok but after days of trying I just cant get the new version to build. ](*,)  I've got all the dependencies built (i think), I get this error at 21% of build when running the build_ubuntu.sh:

simon-0.4.0/build/simonlib/simonvision/../../../simonlib/simonvision/imageanalyzer.h:22:16: fatal error: cv.h: No such file or directory
compilation terminated.
make[2]: *** [simonlib/simonvision/CMakeFiles/simonvision.dir/simonvision_automoc.cpp.o] Error 1
make[1]: *** [simonlib/simonvision/CMakeFiles/simonvision.dir/all] Error 2
make: *** [all] Error 2

cant find any documentation on this problem, please help!!!!
greatful for any assistance

---

### Post by morsedl on 2013-05-30
Oh, yes, I should mention: I built on standard Ubuntu 12.04 LTS  (64-bit), not Kubuntu.  Not that it really matters for what I wrote, as  the problem has to do with opencv2 changes, not KDE vs. Gnome issues.


> **morsedl said:**
> This is probably too late in coming, but for what it's worth:

The problem seems to reside in changes made in opencv, specifically, a new source file structure for opencv2.

I just finished building simon from source...

---

