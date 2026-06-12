---
title: "Google Earth 6 - those terrible fonts!"
date: 2011-04-15
forum: General Help
---

### Post by WarrenL on 2011-04-15
Version 5 of Google Earth was giving me some problems (double-clicking My Places wouldn't work, etc) so I downloaded and installed Version 6.

Most of my problems are now solved, but there's the reappearance of another that seems to be annoying the **** off Linux users all over the web - the terrible fonts GE uses on Linux. From what I can gather it comes down to the QT4 libraries - GE uses its own instead of the system ones. Somebody's even gone to all this trouble:

[http://www.techytalk.info/2009/08/bash-script-google-earth-installation-ugly-fonts-fix/](http://www.techytalk.info/2009/08/bash-script-google-earth-installation-ugly-fonts-fix/)

But it doesn't work on GE6. Does anybody know anything more about how to fix this minor but annoying problem that Google doesn't seem to want to do anything about?

---

### Post by Vaphell on 2011-04-15
[http://www.google.com/support/forum/p/earth/thread?tid=656ef9a98bc427dd&hl=en](http://www.google.com/support/forum/p/earth/thread?tid=656ef9a98bc427dd&hl=en)

try that part with hiding GE versions of QT libs and setting paths to system versions in qt.conf
if you have 64bit system you need to use getlibs on googleearth-bin to install 32bit dependencies (or install all 32bit libs manually)
on my 64bit box i get to see nice fonts but in a second it crashes with meaningless message and some stacktrace in logs, maybe you'll be more lucky.
Googlor people are one of the brightest in the industry but GUI of GE is nothing to write home about - unbelievable.

---

### Post by WarrenL on 2011-04-15
G'day Vaphell,

I got as far as trying that myself, and upon restarting GE I had the joy of about two seconds of a nice-looking GUI before GE crashed and disappeared. I guess if I were smarter I'd know where to look in log files for more information, but I'm always barely flying by the seat of my pants when it comes to computers.

Cheers,
Warren.

---

### Post by nerdy_kid on 2011-04-15
I tried deleting Google Earth's packaged QT libraries, and had the same thing happen to me.  About 1 second of fitting in, then a seg fault.  Run google-earth in a terminal to catch the backtrace.

---

### Post by Vaphell on 2011-04-15
internet says that no fix for this problem exists yet :/ maybe before it crashes i'll take a screenshot to look at from time to time weeping.

Google really should set up proper repos for their linux programs like God commanded.

---

### Post by WarrenL on 2011-04-16
Marko over at techytalk.info responded to my comment and had a good bash at making things work, but failed. Scroll down to see the new comments:

[http://www.techytalk.info/2009/08/bash-script-google-earth-installation-ugly-fonts-fix/](http://www.techytalk.info/2009/08/bash-script-google-earth-installation-ugly-fonts-fix/)

It looks like the Google Monster doesn't really care about us. [IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG]

---

### Post by gongyiliao on 2011-05-27
For those who are using amd64 platform:

In fact, you can just 

install the 32-bit version of libfreeimage3 under /usr/lib32 

then modified your last line of /usr/bin/google-earth as:

export LD_PRELOAD=/usr/lib32/libfreeimage.so.3
LD_LIBRARY_PATH=/usr/lib32:.:$LD_LIBRARY_PATH ./googleearth-bin "$@"

then you have everything:

1. nice anti-alias fonts in GE6
2. GE6 shows Chinese, Japanese, Korean properly.
3. add your findings here.

---

### Post by pros on 2011-08-28
googlearth 6 font rendering issue

Solved in LUCID 64bit

Move to a different location or simply delete following files

/opt/google/earth/free/libQtWebKit.so.4
/opt/google/earth/free/libQtNetwork.so.4
/opt/google/earth/free/libQtGui.so.4
/opt/google/earth/free/libQtCore.so.4

Now you need some 32 bit packages that you can find in [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
install libfreeimage3 32 bit- libfreeimage3_3.10.0-2_i386.deb (uncompress i386 deb and copy in /usr/lib32 following files: libfreeimage.so.3, libfreeimage-3.10.0.so, libfreeimageplus.so.3, libfreeimageplus-3.10.0.so)

install libphonon4_4.6.2-0ubuntu5.2_i386.deb (uncompress i386 deb and copy in /usr/lib32 following files: libphonon.so.4, libphonon.so.4.4, libphonon.so.4.4.0 and finally put in /usr/lib/qt4/plugins/designer file libphononwidgets.so)

change last line of /opt/google/earth/free/googleearth to

export LD_PRELOAD=/usr/lib32/libfreeimage.so.3
LD_LIBRARY_PATH=/usr/lib32:.:$LD_LIBRARY_PATH ./googleearth-bin "$@"

---

### Post by ranjan_mg on 2011-12-13
I am trying to get rid of those terrible fonts.. I cound not find libphononwidgets.so in ubuntu 11.10 repositories

Also, when I try the remaining steps, I got GE to start, with nice looking fonts but when I click on a picture inside GE, nothing is displayed..

---

### Post by ranjan_mg on 2011-12-14
OK>> A bit more googling, I was able to solve..

Needed 
(libqjpeg.so libqgif.so) in plugins/imageformat/ directory

From here...

[http://swyear.blogspot.com/2011/05/run-google-earth-6-on-opensuse.html](http://swyear.blogspot.com/2011/05/run-google-earth-6-on-opensuse.html)

---

### Post by itsjustarumour on 2012-01-14
> **pros said:**
> googlearth 6 font rendering issue

Solved in LUCID 64bit

Move to a different location or simply delete following files

/opt/google/earth/free/libQtWebKit.so.4
/opt/google/earth/free/libQtNetwork.so.4
/opt/google/earth/free/libQtGui.so.4
/opt/google/earth/free/libQtCore.so.4

Now you need some 32 bit packages that you can find in [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
install libfreeimage3 32 bit- libfreeimage3_3.10.0-2_i386.deb (uncompress i386 deb and copy in /usr/lib32 following files: libfreeimage.so.3, libfreeimage-3.10.0.so, libfreeimageplus.so.3, libfreeimageplus-3.10.0.so)

install libphonon4_4.6.2-0ubuntu5.2_i386.deb (uncompress i386 deb and copy in /usr/lib32 following files: libphonon.so.4, libphonon.so.4.4, libphonon.so.4.4.0 and finally put in /usr/lib/qt4/plugins/designer file libphononwidgets.so)

change last line of /opt/google/earth/free/googleearth to

export LD_PRELOAD=/usr/lib32/libfreeimage.so.3
LD_LIBRARY_PATH=/usr/lib32:.:$LD_LIBRARY_PATH ./googleearth-bin "$@"

Worked great for me with Google Earth 6.1.0.4857 Beta and Linux Mint 11.10 64-Bit - so many thanks!  :-)  Obviously the exact lib names varied slightly with being on Oneiric, but the basic procedure was correct - I just pasted whatever I'd got from the relevant .deb files into the relevant folders. Also, I didn't have a libphononwidgets.so, but it didn't seem to matter...

Thanks again!

---

### Post by itsjustarumour on 2012-01-14
Sorry - duplicate post due to slow connection!

---

### Post by ofrog21 on 2012-02-15
Just switched to Ubuntu and even with ubuntu unleashed book to my side I am still struggling to understand how to get things done.

I am using 11.10  and trying to fix the GE font issue.  You have lost me in the quote below.  Any assist would be very apprciated.

> **gongyiliao said:**
> For those who are using amd64 platform:

In fact, you can just 

install the 32-bit version of libfreeimage3 under /usr/lib32 

then modified your last line of /usr/bin/google-earth as:

export LD_PRELOAD=/usr/lib32/libfreeimage.so.3
LD_LIBRARY_PATH=/usr/lib32:.:$LD_LIBRARY_PATH ./googleearth-bin "$@"

then you have everything:

1. nice anti-alias fonts in GE6
2. GE6 shows Chinese, Japanese, Korean properly.
3. add your findings here.

---

### Post by itsjustarumour on 2012-02-16
> **ofrog21 said:**
> Just switched to Ubuntu and even with ubuntu unleashed book to my side I am still struggling to understand how to get things done.

I am using 11.10  and trying to fix the GE font issue.  You have lost me in the quote below.  Any assist would be very apprciated.

Hi Ofrog, and welcome to the forum :)

This fonts issue on Google Earth has been problematical for many people, and on other distros as well as Ubuntu.

Try this link, see if it helps:

[http://www.omgubuntu.co.uk/2012/01/how-to-fix-ugly-fonts-in-google-earth-6-2-on-ubuntu/](http://www.omgubuntu.co.uk/2012/01/how-to-fix-ugly-fonts-in-google-earth-6-2-on-ubuntu/)

---

### Post by AndresChort on 2012-02-29
> **pros said:**
> googlearth 6 font rendering issue

Solved in LUCID 64bit

Move to a different location or simply delete following files

/opt/google/earth/free/libQtWebKit.so.4
/opt/google/earth/free/libQtNetwork.so.4
/opt/google/earth/free/libQtGui.so.4
/opt/google/earth/free/libQtCore.so.4

Now you need some 32 bit packages that you can find in [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
install libfreeimage3 32 bit- libfreeimage3_3.10.0-2_i386.deb (uncompress i386 deb and copy in /usr/lib32 following files: libfreeimage.so.3, libfreeimage-3.10.0.so, libfreeimageplus.so.3, libfreeimageplus-3.10.0.so)

install libphonon4_4.6.2-0ubuntu5.2_i386.deb (uncompress i386 deb and copy in /usr/lib32 following files: libphonon.so.4, libphonon.so.4.4, libphonon.so.4.4.0 and finally put in /usr/lib/qt4/plugins/designer file libphononwidgets.so)

change last line of /opt/google/earth/free/googleearth to

export LD_PRELOAD=/usr/lib32/libfreeimage.so.3
LD_LIBRARY_PATH=/usr/lib32:.:$LD_LIBRARY_PATH ./googleearth-bin "$@"

Worked great on 11.10 64bit
Note: couldn't find file
/usr/lib/qt4/plugins/designer file libphononwidgets.so

Thank you!

Edit: Google Earth version is 6.2.1.6014 (beta)

---

### Post by ramois on 2012-03-03
> **pros said:**
> googlearth 6 font rendering issue

Solved in LUCID 64bit

Move to a different location or simply delete following files

/opt/google/earth/free/libQtWebKit.so.4
/opt/google/earth/free/libQtNetwork.so.4
/opt/google/earth/free/libQtGui.so.4
/opt/google/earth/free/libQtCore.so.4

Now you need some 32 bit packages that you can find in [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
install libfreeimage3 32 bit- libfreeimage3_3.10.0-2_i386.deb (uncompress i386 deb and copy in /usr/lib32 following files: libfreeimage.so.3, libfreeimage-3.10.0.so, libfreeimageplus.so.3, libfreeimageplus-3.10.0.so)

install libphonon4_4.6.2-0ubuntu5.2_i386.deb (uncompress i386 deb and copy in /usr/lib32 following files: libphonon.so.4, libphonon.so.4.4, libphonon.so.4.4.0 and finally put in /usr/lib/qt4/plugins/designer file libphononwidgets.so)

change last line of /opt/google/earth/free/googleearth to

export LD_PRELOAD=/usr/lib32/libfreeimage.so.3
LD_LIBRARY_PATH=/usr/lib32:.:$LD_LIBRARY_PATH ./googleearth-bin "$@"

Many thanks pros, worked great.

---

### Post by QuantikTar on 2012-08-13
Hello,

Using this method to force using system libraries works great in 12.04 with googleearth-package installed (excepts that the GE library path are not in /opt)

But the big problem is tat the "baloon tips" like panoramio images get broken... It seems that the software can't read images at all.

Related to libreeimage? Anyone have a fix?

Regards

---

