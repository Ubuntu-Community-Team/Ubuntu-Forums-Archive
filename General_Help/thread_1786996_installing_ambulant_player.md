---
title: "installing ambulant player"
date: 2011-06-20
forum: General Help
---

### Post by sirmark on 2011-06-20
Hi!
I'm trying to install ambulant player on my Ubuntu 10.04.

I have downloaded ambulat from:
[http://www.ambulantplayer.org/Download200s.shtml](http://www.ambulantplayer.org/Download200s.shtml)

Reading  ~/ambulant-2.2/INSTALL  file:

> 
For Linux desktop you need at least autoconf, automake, GNU gcc
(at least version 4.0), gtk2-devel and/or qt-devel (for graphics),
and alsa-devel (for sound).
After unpacking Ambulant you should first download and build the required
3rd party packages. In third_party_packages, run the following command:

    python build-third-party-packages.py linux
    
This will install all needed packages (insofar they are not installed
on your system yet) in "third_party_packages/installed", and configure
and make will pick them up from there.

(In case the automatic build does not suit your needs: see
third_party_pckages/readme.txt for manual building).
So I install from synaptic: qt-sdk
and install: 
sudo apt-get install libgtk2.0-dev

Now I execute script python with this output:

```

+ Ambulant toplevel directory: /home/sirmark/ambulant-2.2
+ processing: libtool
+ ok: libtool
+ processing: expat
+ ok: expat
+ processing: xerces-c
+ ok: xerces-c
+ processing: faad2
+ ok: faad2
+ processing: xulrunner-sdk
+ failed: xulrunner-sdk
+ processing: ffmpeg
+ ok: ffmpeg
+ processing: SDL
+ ok: SDL
+ processing: live
+ ok: live
+ processing: gettext
+ ok: gettext
+ processing: libxml2
+ ok: libxml2

```Then I run ./configure
```

.....cut......

configure: WARNING: Built with ffmpeg libswscale, therefore under GPL license

```and run make with this output:

> 
xpath_stateplugin.cpp:26:25: error: libxml/tree.h: File o directory non esistente
xpath_stateplugin.cpp:27:26: error: libxml/xpath.h: File o directory non esistente
xpath_stateplugin.cpp:28:35: error: libxml/xpathInternals.h: File o directory non esistente
xpath_stateplugin.cpp:72: error: &#8216;xmlNodePtr&#8217; has not been declared
xpath_stateplugin.cpp:74: error: &#8216;xmlDocPtr&#8217; does not name a type
xpath_stateplugin.cpp:75: error: &#8216;xmlXPathContextPtr&#8217; does not name a type
xpath_stateplugin.cpp:87: error: variable or field &#8216;smil_function_execute&#8217; declared void
xpath_stateplugin.cpp:87: error: &#8216;xmlXPathParserContextPtr&#8217; was not declared in this scope
xpath_stateplugin.cpp:87: error: expected primary-expression before &#8216;int&#8217;
xpath_stateplugin.cpp:687: error: expected &#8216;}&#8217; at end of input
make[2]: *** [xpath_stateplugin.lo] Errore 1
make[2]: uscita dalla directory "/home/sirmark/ambulant-2.2/src/plugins"
make[1]: *** [all-recursive] Errore 1
make[1]: uscita dalla directory "/home/sirmark/ambulant-2.2/src"
make: *** [all-recursive] Errore 1

where is the problem ?

thanks for support!

---

### Post by Yellow Pasque on 2011-06-20
```
sudo apt-get install libxml2-dev xulrunner-dev
```

---

