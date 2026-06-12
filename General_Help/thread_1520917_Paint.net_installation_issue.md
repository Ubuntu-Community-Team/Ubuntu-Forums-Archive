---
title: "Paint.net installation issue"
date: 2010-06-30
forum: General Help
---

### Post by Teabicky on 2010-06-30
Hi,  I am trying to install paint.net using mono via the following website:

[http://code.google.com/p/paint-mono/](http://code.google.com/p/paint-mono/)

Firstly I tried to download the tar.gz file directly from the website and use the ./config command and then I used this walkthrough:

[http://maxmanders.co.uk/linux/a-nice-alternative-to-gimp-on-ubuntu/](http://maxmanders.co.uk/linux/a-nice-alternative-to-gimp-on-ubuntu/)

Each time I have had the same problem which looks like this:


> rich@our-desktop:/tmp/paintdotnet-0.1.63$ ./configure 
Looking for required packages
Checking for revision...
paintdotnet has been configured with 
        prefix = /usr/local
        config = RELEASE_AND_PACKAGE_ANY_CPU

rich@our-desktop:/tmp/paintdotnet-0.1.63$ make
make[1]: Entering directory `/tmp/paintdotnet-0.1.63'
make[1]: Leaving directory `/tmp/paintdotnet-0.1.63'
make[1]: Entering directory `/tmp/paintdotnet-0.1.63/Resources.mui'
make pre-all-local-hook prefix=/usr/local
make[2]: Entering directory `/tmp/paintdotnet-0.1.63/Resources.mui'
make[2]: Leaving directory `/tmp/paintdotnet-0.1.63/Resources.mui'
mkdir -p bin/Release/
make RELEASE_AND_PACKAGE_ANY_CPU_BeforeBuild
make[2]: Entering directory `/tmp/paintdotnet-0.1.63/Resources.mui'
make[2]: Leaving directory `/tmp/paintdotnet-0.1.63/Resources.mui'
gmcs -noconfig -codepage:utf8 -warn:4 -optimize+ -debug -define:DEBUG "-define:TRACE" -out:bin/Release/Resources.mui.exe -target:exe './Stub.cs'      -r:System  
/bin/sh: gmcs: not found
make[1]: *** [bin/Release/Resources.mui.exe] Error 127
make[1]: Leaving directory `/tmp/paintdotnet-0.1.63/Resources.mui'
make: *** [all-recursive] Error 1
rich@our-desktop:/tmp/paintdotnet-0.1.63$ 

I have no idea what this means but would love to get it sorted as I have used paint.net on windows and am sad to say that it is goodbye Gimp!.

Cheers.

---

### Post by Teabicky on 2010-06-30
Here's the fix:

[http://linuxundich.de/en/ubuntu/paint-mono-paint-net-fur-linux/](http://linuxundich.de/en/ubuntu/paint-mono-paint-net-fur-linux/)

It seems I needed to install the appropriate mono files first.  I suppose that figures.

---

