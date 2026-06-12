---
title: "w32codecs &amp; libstdc++"
date: 2009-10-17
forum: General Help
---

### Post by yogich on 2009-10-17
Just upgraded, yesterday, to the Karmic beta.  Everything is working great, so far, except for the following issue:

I have installed libstdc++ from [http://packages.ubuntu.com/jaunty/i386/libstdc++5/download](http://packages.ubuntu.com/jaunty/i386/libstdc++5/download) and also, w32codecs (which gave an error, regarding the libs, prior).  Unfortunately, Kaffeine still will not play an audio stream in asf format: [http://citadelcc-wmal-am.wm.llnwd.net/citadelcc_WMAL_AM?MSWMExt=.asf](http://citadelcc-wmal-am.wm.llnwd.net/citadelcc_WMAL_AM?MSWMExt=.asf)

In addition, I have also created /usr/lib32 & copied the two files in libstdc++ to that folder (based on a thread from a printer forum), in hopes that would fix the problem.  Still, nothing happens, except a box, with a large red 'X' and nothing else but the 'OK' button, when kaffeine loads & tries to play the stream.

I have done a deliberate search --"w32codecs"-- through the forum, and this particular issue, is not covered, apparently.  Been using Kubuntu/Ubuntu, for two or three years, and never encountered this problem.  Have I missed, something?  

Any help, most appreciated.

---

### Post by hal10000 on 2009-10-17
try sudo apt-get install non-free-codecs instead
Are you using 32bit system?

---

