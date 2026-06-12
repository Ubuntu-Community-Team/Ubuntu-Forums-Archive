---
title: "libCURL not found"
date: 2009-07-31
forum: General Help
---

### Post by toleolu on 2009-07-31
First off, total noob here, so be kind :D

I'm trying to install a program that unfortunately is not available through Synaptic. Program is called TaxiDraw and is used in conjunction with Flight Gear to edit airport runway and taxiway details.

Anyway when I run ./configure, I get:

checking curl/curl.h usability... no
checking curl/curl.h presence... no
checking for curl/curl.h... no

libCURL not found
configure aborted.

I did find curl in Synaptic and installed that, but that didn't fix the problem. 

Any suggestions welcomed. Thanks

---

### Post by guillaume_u on 2009-07-31
Hi,

I'm not an expert myselft, but usually, to compile software, you need some development packages.

In your case, with libcurl, you would go to Synaptic and search libcurl. Then in the results, you would see :

libcurl4-gnutls-dev - Development files and documentation for libcurl (GnuTLS)
libcurl4-openssl-dev - Development files and documentation for libcurl (OpenSSL)

with the following descriptions:

"These files (ie. includes, static library, manual pages) allow to
build software which uses libcurl."

Check whether these are installed and retry. Hopefully it'll work.

---

### Post by toleolu on 2009-07-31
Thanks, that was part of my problem. I installed the GnuTLS and was able to run configure after that. Problem now is make is dying. I get:

make[2]: *** [ground.o] Error 1
make[2]: Leaving directory `/home/charles/Desktop/TaxiDraw-0.3.2/src/AI'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/charles/Desktop/TaxiDraw-0.3.2/src'
make: *** [all-recursive] Error 1

when I run make.

Interesting thing I noticed when I installed, GnuTLS, if I clicked on OpenSSL to install it as well, it would uncheck GnuTLS and vice versa, if I clicked on GnuTLS it would uncheck OpenSSL. Are the packages incompatible with each other, or can you just only install them one at a time. A little hesitant to do too much more because my inexperience already has this Ubuntu install pretty jacked up. Probably gonna have to wipe it at some point and start all over again anyway.

---

### Post by mc4man on 2009-07-31
you should post what version of ubuntu you're using.

I believe the error is from the version of libwxgtk (wx-config) that your using (it's too new

You can have different versions installed, then you use a command to pick the 'current one.

I'm on hardy so the default would be the 2.8 version, though I also happen to have 2.4 and 2.6 installed

So search wx in synaptic and look for libwxgtk2.4-dev and install it.

Then run this in a terminal 
```
sudo update-alternatives --config wx-config
```

Look for the entry in quote below marked in blue, pick the appropriate number, press enter (your number may be different, I entered 6

You want to see the line marked in red after choosing number and pressing enter

> doug@doug-laptop:~$ sudo update-alternatives --config wx-config

There are 6 alternatives which provide `wx-config'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/lib/wx/config/base-unicode-release-2.6
          2    /usr/lib/wx/config/gtk2-unicode-release-2.6
          3    /usr/lib/wx/config/base-unicode-release-2.8
 *+       4    /usr/lib/wx/config/gtk2-unicode-release-2.8
          5    /usr/bin/wxbase-2.4-config
          6    [COLOR="Blue"]/usr/bin/wxgtk-2.4-config
[/COLOR]
Press enter to keep the default[*], or type selection number: 6
[COLOR="Red"]Using '/usr/bin/wxgtk-2.4-config'[/COLOR] to provide 'wx-config'.

(( note that * shows current, + the default, 

Then run this on your source and then ./configure, make

```
make distclean
```

That should get you to almost done, I see one error I'm not 100% sure how to fix.

If you get this, post back
> In file included from TaxiDrawApp.cpp:6:
TaxiDrawFrame.h:113: error: extra qualification &#8216;TDFrame::&#8217; on member &#8216;EnableAirportMenuItems&#8217;


I 'fixed' it by editing line 113 in TaxiDrawFrame.h ,(but maybe not properly though the source built, made a checkinstall .deb and seems to run ok.
Someone you knows more may offer a better/proper edit (took an uneducated guess

Orig. line
> void TDFrame::EnableAirportMenuItems(bool b);

Edit
> 
void EnableAirportMenuItems(bool b);

If it makes clean for you you could install checkinstall and go at a min after the make (instead of sudo make install 
```
sudo checkinstall --fstrans=no
```

Advantage of checkinstall is it's easy to remove if need be

 > Done. The new package has been installed and saved to

 /home/doug/Desktop/fly/TaxiDraw-0.3.2/taxidraw_0.3.2-1_i386.deb

 You can remove it from your system anytime using: 

      dpkg -r taxidraw

---

### Post by guillaume_u on 2009-07-31
Unfortunately, you're unveiling my incompetence already.

However, could you post a few more lines of the output of make. There must be some clues about why it got some errors.

About the two packages, if installing one removes the other, it's probably for your own good. Did you try to run make with the openssl version. What is the output?

---

### Post by toleolu on 2009-07-31
Thanks, I will give your suggestions a shot. I'm on Ubuntu 9.04, clean install not an upgrade, and I have had some problems with files and libraries missing.

Thanks again, I will post back when I'm done.

---

### Post by toleolu on 2009-07-31
Here's the full text of what I am getting when I run make:]

root@charles-desktop:/home/charles/Desktop/TaxiDraw-0.3.2# make
Making all in src
make[1]: Entering directory `/home/charles/Desktop/TaxiDraw-0.3.2/src'
Making all in AI
make[2]: Entering directory `/home/charles/Desktop/TaxiDraw-0.3.2/src/AI'
 g++ -DPACKAGE_NAME="" -DPACKAGE_TARNAME="" -DPACKAGE_VERSION="" -DPACKAGE_STRING="" -DPACKAGE_BUGREPORT="" -DPACKAGE="TaxiDraw" -DVERSION="0.3.2" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DSTDC_HEADERS=1 -DHAVE_FCNTL_H=1 -DHAVE_GETOPT_H=1 -DHAVE_MALLOC_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STDLIB_H=1 -DHAVE_SYS_PARAM_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_SYS_TIME_H=1 -DHAVE_SYS_TIMEB_H=1 -DHAVE_UNISTD_H=1 -DHAVE_VALUES_H=1 -DTIME_WITH_SYS_TIME=1 -DRETSIGTYPE=void -DHAVE_VPRINTF=1 -DHAVE_FTIME=1 -DHAVE_GETTIMEOFDAY=1 -DHAVE_TIMEGM=1 -DHAVE_MEMCPY=1 -DHAVE_BCOPY=1 -DHAVE_MKTIME=1 -DHAVE_STRSTR=1 -DHAVE_RAND=1 -DHAVE_MKFIFO=1 -DHAVE_RANDOM=1 -DHAVE_DRAND48=1 -DHAVE_SETITIMER=1 -DHAVE_GETITIMER=1 -DHAVE_SIGNAL=1 -DHAVE_GETRUSAGE=1  -I. -I. -I../../src  -I/usr/lib/wx/include/gtk2-unicode-release-2.8 -I/usr/include/wx-2.8 -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -D__WXGTK__  -g -O2 -I/usr/lib/wx/include/gtk2-unicode-release-2.8 -I/usr/include/wx-2.8 -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -D__WXGTK__ -MT ground.o -MD -MP -MF .deps/ground.Tpo -c -o ground.o ground.cpp
In file included from ground.cpp:33:
ground.h:56: warning: &#8216;typedef&#8217; was ignored in this declaration
ground.h:64: warning: &#8216;typedef&#8217; was ignored in this declaration
ground.h:83: warning: &#8216;typedef&#8217; was ignored in this declaration
ground.cpp: In member function &#8216;bool FGGround::LoadNetwork(const char*)&#8217;:
ground.cpp:129: warning: deprecated conversion from string constant to &#8216;char*&#8217;
ground.cpp:204: warning: deprecated conversion from string constant to &#8216;char*&#8217;
ground.cpp: In member function &#8216;arc* FGGround::GetClosestArcXY(Point3D, double&)&#8217;:
ground.cpp:341: error: conversion from &#8216;const char [23]&#8217; to &#8216;const wxString&#8217; is ambiguous
/usr/include/wx-2.8/wx/string.h:692: note: candidates are: wxString::wxString(wxChar, size_t) <near match>
/usr/include/wx-2.8/wx/string.h:682: note:                 wxString::wxString(int) <near match>
ground.cpp:348: error: conversion from &#8216;const char [23]&#8217; to &#8216;const wxString&#8217; is ambiguous
/usr/include/wx-2.8/wx/string.h:692: note: candidates are: wxString::wxString(wxChar, size_t) <near match>
/usr/include/wx-2.8/wx/string.h:682: note:                 wxString::wxString(int) <near match>
ground.cpp:351: error: conversion from &#8216;const char [46]&#8217; to &#8216;const wxString&#8217; is ambiguous
/usr/include/wx-2.8/wx/string.h:692: note: candidates are: wxString::wxString(wxChar, size_t) <near match>
/usr/include/wx-2.8/wx/string.h:682: note:                 wxString::wxString(int) <near match>
make[2]: *** [ground.o] Error 1
make[2]: Leaving directory `/home/charles/Desktop/TaxiDraw-0.3.2/src/AI'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/charles/Desktop/TaxiDraw-0.3.2/src'
make: *** [all-recursive] Error 1

I'm gonna try mc4man's suggestion and post back.

Thanks

---

### Post by toleolu on 2009-07-31
Ok, make was clean, I then dowloaded and installed checkinstall, ran it, and got this:

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

Please write a description for the package.
End your description with an empty line or EOF.
>> TaxiDrawInstall
>> 

*****************************************
**** Debian package creation selected ***
*****************************************

*** Warning: The package name "TaxiDraw" contains upper case
*** Warning: letters. dpkg might not like that so I changed
*** Warning: them to lower case.

This package will be built according to these values: 

0 -  Maintainer: [ root@charles-desktop ]
1 -  Summary: [ TaxiDrawInstall ]
2 -  Name:    [ taxidraw ]
3 -  Version: [ 0.3.2 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ TaxiDraw-0.3.2 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]
11 - Provides: [ taxidraw ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make...Installing with install...

========================= Installation results ===========================
Making install in src
make[1]: Entering directory `/home/charles/Desktop/TaxiDraw-0.3.2/src'
Making install in AI
make[2]: Entering directory `/home/charles/Desktop/TaxiDraw-0.3.2/src/AI'
make[3]: Entering directory `/home/charles/Desktop/TaxiDraw-0.3.2/src/AI'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/charles/Desktop/TaxiDraw-0.3.2/src/AI'
make[2]: Leaving directory `/home/charles/Desktop/TaxiDraw-0.3.2/src/AI'
Making install in Airport
make[2]: Entering directory `/home/charles/Desktop/TaxiDraw-0.3.2/src/Airport'
make[3]: Entering directory `/home/charles/Desktop/TaxiDraw-0.3.2/src/Airport'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/charles/Desktop/TaxiDraw-0.3.2/src/Airport'
make[2]: Leaving directory `/home/charles/Desktop/TaxiDraw-0.3.2/src/Airport'
Making install in Dialogs
make[2]: Entering directory `/home/charles/Desktop/TaxiDraw-0.3.2/src/Dialogs'
make[3]: Entering directory `/home/charles/Desktop/TaxiDraw-0.3.2/src/Dialogs'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/charles/Desktop/TaxiDraw-0.3.2/src/Dialogs'
make[2]: Leaving directory `/home/charles/Desktop/TaxiDraw-0.3.2/src/Dialogs'
Making install in Math
make[2]: Entering directory `/home/charles/Desktop/TaxiDraw-0.3.2/src/Math'
make[3]: Entering directory `/home/charles/Desktop/TaxiDraw-0.3.2/src/Math'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/charles/Desktop/TaxiDraw-0.3.2/src/Math'
make[2]: Leaving directory `/home/charles/Desktop/TaxiDraw-0.3.2/src/Math'
Making install in Projection
make[2]: Entering directory `/home/charles/Desktop/TaxiDraw-0.3.2/src/Projection'
make[3]: Entering directory `/home/charles/Desktop/TaxiDraw-0.3.2/src/Projection'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/charles/Desktop/TaxiDraw-0.3.2/src/Projection'
make[2]: Leaving directory `/home/charles/Desktop/TaxiDraw-0.3.2/src/Projection'
Making install in Main
make[2]: Entering directory `/home/charles/Desktop/TaxiDraw-0.3.2/src/Main'
 g++ -DPACKAGE_NAME="" -DPACKAGE_TARNAME="" -DPACKAGE_VERSION="" -DPACKAGE_STRING="" -DPACKAGE_BUGREPORT="" -DPACKAGE="TaxiDraw" -DVERSION="0.3.2" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DSTDC_HEADERS=1 -DHAVE_FCNTL_H=1 -DHAVE_GETOPT_H=1 -DHAVE_MALLOC_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STDLIB_H=1 -DHAVE_SYS_PARAM_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_SYS_TIME_H=1 -DHAVE_SYS_TIMEB_H=1 -DHAVE_UNISTD_H=1 -DHAVE_VALUES_H=1 -DTIME_WITH_SYS_TIME=1 -DRETSIGTYPE=void -DHAVE_VPRINTF=1 -DHAVE_FTIME=1 -DHAVE_GETTIMEOFDAY=1 -DHAVE_TIMEGM=1 -DHAVE_MEMCPY=1 -DHAVE_BCOPY=1 -DHAVE_MKTIME=1 -DHAVE_STRSTR=1 -DHAVE_RAND=1 -DHAVE_MKFIFO=1 -DHAVE_RANDOM=1 -DHAVE_DRAND48=1 -DHAVE_SETITIMER=1 -DHAVE_GETITIMER=1 -DHAVE_SIGNAL=1 -DHAVE_GETRUSAGE=1  -I. -I. -I../../src  -I/usr/lib/wx/include/gtk-2.4 -DGTK_NO_CHECK_CASTS -D__WXGTK__ -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES  -g -O2 -I/usr/lib/wx/include/gtk-2.4 -DGTK_NO_CHECK_CASTS -D__WXGTK__ -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -MT TaxiDrawApp.o -MD -MP -MF .deps/TaxiDrawApp.Tpo -c -o TaxiDrawApp.o TaxiDrawApp.cpp
In file included from ../../src/Airport/airport.h:14,
                 from TaxiDrawCanvas.h:10,
                 from TaxiDrawFrame.h:6,
                 from TaxiDrawApp.cpp:6:
../../src/AI/ground.h:56: warning: ‘typedef’ was ignored in this declaration
../../src/AI/ground.h:64: warning: ‘typedef’ was ignored in this declaration
../../src/AI/ground.h:83: warning: ‘typedef’ was ignored in this declaration
In file included from TaxiDrawApp.cpp:6:
TaxiDrawFrame.h:113: error: extra qualification ‘TDFrame::’ on member ‘EnableAirportMenuItems’
make[2]: *** [TaxiDrawApp.o] Error 1
make[2]: Leaving directory `/home/charles/Desktop/TaxiDraw-0.3.2/src/Main'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/charles/Desktop/TaxiDraw-0.3.2/src'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Restoring overwritten files from backup...OK

Cleaning up...OK

Bye.

Needless to say, I have no idea what any of that means, but thanks in advance for your help and patience.

---

### Post by toleolu on 2009-07-31
Oh by the way, I'm doing this logged in as root, and the files are on home/charles/Desktop. 

Don't know if that has anything to do with anything, just thought I would mention it.

Thanks again.

---

### Post by toleolu on 2009-07-31
OK, something new. I went back to Taxi Draws website and found this:

cvs -d :pserver:anonymous@taxidraw.cvs.sourceforge.net:/cvsroot/taxidraw login
Enter a blank password (just hit return) when prompted for a password. cvs -z3 -d :pserver:anonymous@taxidraw.cvs.sourceforge.net:/cvsroot/taxidraw co TaxiDraw To compile the CVS code: ./autogen.sh
./configure
make
make install
No errors during autogen or configure, but when I ran make (God I love make) I get:

root@charles-desktop:~/TaxiDraw# make
Making all in src
make[1]: Entering directory `/root/TaxiDraw/src'
make  all-recursive
make[2]: Entering directory `/root/TaxiDraw/src'
Making all in AI
make[3]: Entering directory `/root/TaxiDraw/src/AI'
g++ -DHAVE_CONFIG_H -I. -I../../src -I../../src  -I/usr/lib/wx/include/gtk-2.4 -DGTK_NO_CHECK_CASTS -D__WXGTK__ -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES  -g -O2 -I/usr/lib/wx/include/gtk-2.4 -DGTK_NO_CHECK_CASTS -D__WXGTK__ -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -MT AIGroundNetworkLoader.o -MD -MP -MF .deps/AIGroundNetworkLoader.Tpo -c -o AIGroundNetworkLoader.o AIGroundNetworkLoader.cpp
In file included from ../../src/Airport/Airport.h:18,
                 from AIGroundNetworkLoader.h:4,
                 from AIGroundNetworkLoader.cpp:1:
../../src/Map/MapObjectContainer.h: In member function ‘size_t MapObjectContainer::GetObjectCount() const’:
../../src/Map/MapObjectContainer.h:69: error: ‘const class MapObjectList’ has no member named ‘size’
In file included from AIGroundNetworkLoader.cpp:5:
StartupLocationMapObject.h: In member function ‘bool StartupLocationMapObject::hasPushbackRoute()’:
StartupLocationMapObject.h:69: error: ‘class AINetworkVertexNodes’ has no member named ‘size’
make[3]: *** [AIGroundNetworkLoader.o] Error 1
make[3]: Leaving directory `/root/TaxiDraw/src/AI'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/root/TaxiDraw/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/root/TaxiDraw/src'
make: *** [all-recursive] Error 1
root@charles-desktop:~/TaxiDraw# cvs update -dPA
? src/stamp-h1
cvs update: Updating .
cvs update: Updating docs
cvs update: Updating docs/images
cvs update: Updating msvc
cvs update: Updating msvc/6.0
cvs update: Updating msvc/7.1
cvs update: Updating msvc/8.0
cvs update: Updating src
cvs update: Updating src/AI
cvs update: Updating src/Airport
cvs update: Updating src/Dialogs
cvs update: Updating src/IO
cvs update: Updating src/Imagery
cvs update: Updating src/Main
cvs update: Updating src/Main/Modes
cvs update: Updating src/Main/icons
cvs update: Updating src/Map
cvs update: Updating src/Math
cvs update: Updating src/Modes
cvs update: Updating src/Projection
cvs update: Updating src/Transactions
cvs update: Updating src/exceptions
cvs update: Updating src/wx
cvs update: Updating src/wx/menutoolbar
cvs update: Updating src/wx/propgrid
cvs update: Updating src/xml
root@charles-desktop:~/TaxiDraw# make
Making all in src
make[1]: Entering directory `/root/TaxiDraw/src'
make  all-recursive
make[2]: Entering directory `/root/TaxiDraw/src'
Making all in AI
make[3]: Entering directory `/root/TaxiDraw/src/AI'
g++ -DHAVE_CONFIG_H -I. -I../../src -I../../src  -I/usr/lib/wx/include/gtk-2.4 -DGTK_NO_CHECK_CASTS -D__WXGTK__ -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES  -g -O2 -I/usr/lib/wx/include/gtk-2.4 -DGTK_NO_CHECK_CASTS -D__WXGTK__ -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -MT AIGroundNetworkLoader.o -MD -MP -MF .deps/AIGroundNetworkLoader.Tpo -c -o AIGroundNetworkLoader.o AIGroundNetworkLoader.cpp
In file included from ../../src/Airport/Airport.h:18,
                 from AIGroundNetworkLoader.h:4,
                 from AIGroundNetworkLoader.cpp:1:
../../src/Map/MapObjectContainer.h: In member function ‘size_t MapObjectContainer::GetObjectCount() const’:
../../src/Map/MapObjectContainer.h:69: error: ‘const class MapObjectList’ has no member named ‘size’
In file included from AIGroundNetworkLoader.cpp:5:
StartupLocationMapObject.h: In member function ‘bool StartupLocationMapObject::hasPushbackRoute()’:
StartupLocationMapObject.h:69: error: ‘class AINetworkVertexNodes’ has no member named ‘size’
make[3]: *** [AIGroundNetworkLoader.o] Error 1
make[3]: Leaving directory `/root/TaxiDraw/src/AI'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/root/TaxiDraw/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/root/TaxiDraw/src'
make: *** [all-recursive] Error 1
root@charles-desktop:~/TaxiDraw# 

I tried run the synch below, just for the heck of it:

To synchronise your CVS checkout with the latest code: cvs update -dPA

but when I run make I still get the same error.

Thanks

---

### Post by mc4man on 2009-07-31
From your attempt on the 0.3.2 source (using wxgtk-2.4

> TaxiDrawFrame.h:113: error: extra qualification &#8216;TDFrame::&#8217; on member &#8216;EnableAirportMenuItems&#8217;

note the edit I mentioned (do before the make or configure, file is in TaxiDraw-0.3.2/src/Main

For the cvs you need  to switch to wxgtk-2.6
> doug@doug-laptop:~$ sudo update-alternatives --config wx-config

There are 6 alternatives which provide `wx-config'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/lib/wx/config/base-unicode-release-2.6
*         2   [COLOR="Blue"] /usr/lib/wx/config/gtk2-unicode-release-2.6[/COLOR]
          3    /usr/lib/wx/config/base-unicode-release-2.8
 +        4    /usr/lib/wx/config/gtk2-unicode-release-2.8
          5    /usr/bin/wxgtk-2.4-config
          6    /usr/bin/wxbase-2.4-config




Noting that there are alot of warning's though it does build cleanly (for a checkinstall deb of the cvs you need to give a version, 1 will do

I don't have the time atm, you could try the cvs with wx 2.8 or 2.6 base ect., maybe less warnings (though it did build fine

I wouldn't build as root, just install as root (build in home or desktop

from the cvs, no edit in that one source file needed like in the 0.3.2 source 
 > Done. The new package has been installed and saved to

 /home/doug/Desktop/fly2/TaxiDraw/taxidraw_[COLOR="Blue"]1-1[/COLOR]_i386.deb

 You can remove it from your system anytime using: 

      dpkg -r taxidraw


Edit:
the cvs version seems a little more 'polished' than the 0.3.2, I'd go that way (the other didn't open with a 'wizard', see screen) or build both and try

---

### Post by mc4man on 2009-07-31
Was curious, the cvs builds the same with the 2.8 version as it did with the 2.6
> There are 6 alternatives which provide `wx-config'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/lib/wx/config/base-unicode-release-2.6
*         2    /usr/lib/wx/config/gtk2-unicode-release-2.6
          3    /usr/lib/wx/config/base-unicode-release-2.8
 +        4    /usr/lib/wx/config/gtk2-unicode-release-2.8
          5    /usr/bin/wxgtk-2.4-config
          6    /usr/bin/wxbase-2.4-config

Press enter to keep the default[*], or type selection number: 4
Using '/usr/lib/wx/config/gtk2-unicode-release-2.8' to provide 'wx-config'


list of commands used, from your normal prompt (not root (I like to build in a separate folder in home

 >  mkdir fly1
  cd fly1
  cvs -d :pserver:anonymous@taxidraw.cvs.sourceforge.net:/cvsroot/taxidraw login
  cvs -z3 -d :pserver:anonymous@taxidraw.cvs.sourceforge.net:/cvsroot/taxidraw co TaxiDraw
cd TaxiDraw
./autogen.sh
 ./configure
 make
 sudo checkinstall --fstrans=no


Checkinstall will prompt you to give a version number 

(( a version number can be added to the checkinstall command, I hardly ever use checkinstall so not up on exact syntax, others are, but  the prompt will do just fine, as mentioned, using 1 will suffice

If you make a dir. (folder) to build in never have spaces in the name, either 1 'word' or use _ between words


Note: run a make distclean on your source or start with fresh one after changing your wx-config version

---

### Post by toleolu on 2009-08-02
SUCCESS AT LAST:popcorn:

Thanks for all your help, doing it as a deb package did the trick.

I have read that anytime you can convert something to .deb you're better off doing so rather than running make, is that correct??

Thanks again, I learned a lot.

---

### Post by mc4man on 2009-08-02
> I have read that anytime you can convert something to .deb you're better off doing so rather than [COLOR="Blue"]running make[/COLOR], is that correct??

That would be make install (sudo make install

Generally speaking yes, for a number of reasons
The app will be easier to remove and or upgrade to newer/higher version
Will show up in the package manager (synaptic

Your also free to delete the source folder, with a sudo make install many times you'll need to keep it to run a sudo make uninstall (some sources will have no make uninstall, in those cases removal has to be done manually

You'll notice a file or 2 that checkinstall created that are locked, including your deb. (owned by root, to delete use gksudo nautilus

(( I think there are options for checkinstall that can prevent that, no big deal either way

Some sources cannot be built into .debs by checkinstall, in those cases a sudo make install is what you'll need to use (or build a 'proper' debian package or package set

---

### Post by toleolu on 2009-08-03
Can you build a ubuntu compatible deb package for just about anything??

I found this tutorial:

[http://forums.debian.net/viewtopic.php?f=16&t=38976](http://forums.debian.net/viewtopic.php?f=16&t=38976)

and am assuming that process can be used to create deb packages for Ubuntu, is that right??

One question I have is when they talk about source, I know they are referring to the program source code, but is that the same thing as CVS??

Thanks

---

