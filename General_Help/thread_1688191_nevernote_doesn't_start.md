---
title: "nevernote doesn't start"
date: 2011-02-15
forum: General Help
---

### Post by arapaho on 2011-02-15
I installed Nevernote from nevernote-0.95_i386.deb and it doesn't start.
There is a topic about Nevernote but seems to be closed, so I start this one.
[http://ubuntuforums.org/showthread.php?t=1523333&page=9](http://ubuntuforums.org/showthread.php?t=1523333&page=9)
```
/usr/share/nevernote $ ./nevernote.sh
Exception in thread "main" java.lang.ExceptionInInitializerError
	at com.trolltech.qt.QtJambiObject.<clinit>(QtJambiObject.java:60)
Caused by: java.lang.RuntimeException: Loading library failed, progress so far:
Unpacking .jar file: 'qtjambi-linux32-gcc-4.5.2_01.jar'
Checking Archive 'qtjambi-linux32-gcc-4.5.2_01.jar'
 - cache key='gcc-20090628-0950'
 - adding 'libstdc++.so.6' to library map
 - library: name='lib/libstdc++.so.6', 
 - adding 'libQtCore.so.4' to library map
 - library: name='lib/libQtCore.so.4', 
 - adding 'libQtGui.so.4' to library map
 - library: name='lib/libQtGui.so.4', 
 - adding 'libQtXml.so.4' to library map
 - library: name='lib/libQtXml.so.4', 
 - adding 'libQtSql.so.4' to library map
 - library: name='lib/libQtSql.so.4', 
 - adding 'libQtSvg.so.4' to library map
 - library: name='lib/libQtSvg.so.4', 
 - adding 'libQtNetwork.so.4' to library map
 - library: name='lib/libQtNetwork.so.4', 
 - adding 'libQtOpenGL.so.4' to library map
 - library: name='lib/libQtOpenGL.so.4', 
 - adding 'libQtWebKit.so.4' to library map
 - library: name='lib/libQtWebKit.so.4', 
 - adding 'libQtXmlPatterns.so.4' to library map
 - library: name='lib/libQtXmlPatterns.so.4', 
 - adding 'libphonon.so.4' to library map
 - library: name='lib/libphonon.so.4', 
 - library: name='plugins/phonon_backend/libphonon_gstreamer.so', never load
 - library: name='plugins/imageformats/libqjpeg.so', never load
 - library: name='plugins/imageformats/libqgif.so', never load
 - library: name='plugins/imageformats/libqmng.so', never load
 - library: name='plugins/imageformats/libqtiff.so', never load
 - library: name='plugins/imageformats/libqsvg.so', never load
 - library: name='plugins/iconengines/libqsvgicon.so', never load
 - library: name='plugins/codecs/libqcncodecs.so', never load
 - library: name='plugins/codecs/libqjpcodecs.so', never load
 - library: name='plugins/codecs/libqkrcodecs.so', never load
 - library: name='plugins/codecs/libqtwcodecs.so', never load
 - library: name='plugins/accessible/libqtaccessiblewidgets.so', never load
 - library: name='plugins/sqldrivers/libqsqlite.so', never load
 - adding 'libqtjambi.so' to library map
 - library: name='lib/libqtjambi.so', 
 - adding 'libcom_trolltech_qt_core.so' to library map
 - library: name='lib/libcom_trolltech_qt_core.so', 
 - adding 'libcom_trolltech_qt_gui.so' to library map
 - library: name='lib/libcom_trolltech_qt_gui.so', 
 - adding 'libcom_trolltech_qt_xml.so' to library map
 - library: name='lib/libcom_trolltech_qt_xml.so', 
 - adding 'libcom_trolltech_qt_sql.so' to library map
 - library: name='lib/libcom_trolltech_qt_sql.so', 
 - adding 'libcom_trolltech_qt_svg.so' to library map
 - library: name='lib/libcom_trolltech_qt_svg.so', 
 - adding 'libcom_trolltech_qt_network.so' to library map
 - library: name='lib/libcom_trolltech_qt_network.so', 
 - adding 'libcom_trolltech_qt_opengl.so' to library map
 - library: name='lib/libcom_trolltech_qt_opengl.so', 
 - adding 'libcom_trolltech_qt_phonon.so' to library map
 - library: name='lib/libcom_trolltech_qt_phonon.so', 
 - adding 'libcom_trolltech_qt_webkit.so' to library map
 - library: name='lib/libcom_trolltech_qt_webkit.so', 
 - adding 'libcom_trolltech_qt_xmlpatterns.so' to library map
 - library: name='lib/libcom_trolltech_qt_xmlpatterns.so', 
 - plugin path='plugins'
 - using cache directory: '/tmp/QtJambi_magenta_i386_4.5.2_01_gcc-20090628-0950'
 - cache directory exists
Loading library: 'libQtCore.so.4'...
 - using deployment spec

	at com.trolltech.qt.internal.NativeLibraryManager.loadNativeLibrary(NativeLibraryManager.java:431)
	at com.trolltech.qt.internal.NativeLibraryManager.loadQtLibrary(NativeLibraryManager.java:355)
	at com.trolltech.qt.Utilities.loadQtLibrary(Utilities.java:140)
	at com.trolltech.qt.Utilities.loadQtLibrary(Utilities.java:136)
	at com.trolltech.qt.QtJambi_LibraryInitializer.<clinit>(QtJambi_LibraryInitializer.java:56)
	... 1 more
Caused by: java.lang.UnsatisfiedLinkError: /tmp/QtJambi_magenta_i386_4.5.2_01_gcc-20090628-0950/lib/libQtCore.so.4: /tmp/QtJambi_magenta_i386_4.5.2_01_gcc-20090628-0950/lib/libQtCore.so.4: failed to map segment from shared object: Operation not permitted
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1750)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1646)
	at java.lang.Runtime.load0(Runtime.java:787)
	at java.lang.Runtime.load(Runtime.java:775)
	at com.trolltech.qt.internal.NativeLibraryManager.loadLibrary_helper(NativeLibraryManager.java:458)
	at com.trolltech.qt.internal.NativeLibraryManager.loadNativeLibrary(NativeLibraryManager.java:426)
	... 5 more
Could not find the main class: cx.fbn.nevernote.NeverNote. Program will exit.
/usr/share/nevernote

```

---

### Post by baumgarr on 2011-02-15
I've never seen this error.  It is happening when Jambi tries to load before NeverNote even really starts.  I think it is failing to find some of the Qt libraries.

The first thing I'd verify is that you are running the 32 bit Java JVM.  I don't think this is the problem or you'd get a different error, but it is something to check.

Validate the contents of /usr/share/nevernote/lib.  You should have 2 Qt libraries in that directory.

I did find one thread which had a similar problem.  It looks like they added LD_LIBRARY_PATH=/usr/lib/jni to their profile.  That might work.

If nothing else I can try to recreate the problem, but I'd need to know what JVM, the version of Mint you are running, if you are using 64 or 32 bit, and what window manager you are using.  I'd also like to know if you are on a netbook or some other resource constrained machine.

---

### Post by arapaho on 2011-02-15
Thank you for your quick response.
I'm currently running Linux Mint 9 Isadora 32-bit on PC (no laptop or anything unusual)
2.6.32-28-generic #55-Ubuntu i686 GNU/Linux
I have:
pyhton-qt4 version 4.7.2-0ubuntu1
sun-java6-bin version 6.22-0ubuntu1~10.04
window manager Gtk2
In /usr/share/nevernote/lib I have: qtjambi-linux32-4.5.2_01.jar and qtjambi-linux32-gcc-4.5.2_01.jar

```
/usr/share/nevernote/lib $ ls -la
razem 53716
drwxr-xr-x 2 root root     4096 2011-02-14 18:54 .
drwxr-xr-x 8 root root     4096 2011-02-14 18:54 ..
-rw-r--r-- 1 root root   345048 2010-12-19 21:35 apache-mime4j-0.6.jar
-rw-r--r-- 1 root root    46725 2010-12-19 21:35 commons-codec-1.3.jar
-rw-r--r-- 1 root root   161361 2010-12-19 21:35 commons-compress-1.1.jar
-rw-r--r-- 1 root root   258299 2010-12-19 21:35 commons-lang-2.4.jar
-rw-r--r-- 1 root root    60686 2010-12-19 21:35 commons-logging-1.1.1.jar
-rw-r--r-- 1 root root  3427882 2010-12-19 21:35 evernote.jar
-rw-r--r-- 1 root root  1198447 2010-12-19 21:35 h2-1.2.136.jar
-rw-r--r-- 1 root root   292893 2010-12-19 21:35 httpclient-4.0.3.jar
-rw-r--r-- 1 root root   172888 2010-12-19 21:35 httpcore-4.0.1.jar
-rw-r--r-- 1 root root    25447 2010-12-19 21:35 httpmime-4.0.3.jar
-rw-r--r-- 1 root root   223395 2010-12-19 21:35 jaxen-1.1.3.jar
-rw-r--r-- 1 root root   171297 2010-12-19 21:35 jazzy.jar
-rw-r--r-- 1 root root   188121 2010-12-19 21:35 jtidy-r938.jar
-rw-r--r-- 1 root root   148485 2010-12-19 21:35 libthrift.jar
-rw-r--r-- 1 root root   367444 2010-12-19 21:35 log4j-1.2.14.jar
-rw-r--r-- 1 root root     2524 2010-12-19 21:35 log4j.properties
-rw-r--r-- 1 root root  9918863 2010-12-19 21:35 pdfbox-app-1.3.1.jar
-rw-r--r-- 1 root root  2087109 2010-12-19 21:35 PDFRenderer.jar
-rw-r--r-- 1 root root  1675036 2010-12-19 21:35 poi-3.7-20101029.jar
-rw-r--r-- 1 root root   498259 2010-12-19 21:35 poi-ooxml-3.7.jar
-rw-r--r-- 1 root root  3967696 2010-12-19 21:35 poi-ooxml-schemas-3.7-20101029.jar
-rw-r--r-- 1 root root   840218 2010-12-19 21:35 poi-scratchpad-3.7-20101029.jar
-rw-r--r-- 1 root root  2759733 2010-12-19 21:35 qtjambi-linux32-4.5.2_01.jar
-rw-r--r-- 1 root root 21724550 2010-12-19 21:35 qtjambi-linux32-gcc-4.5.2_01.jar
-rw-r--r-- 1 root root  1490238 2010-12-19 21:35 tika.jar
-rw-r--r-- 1 root root  2666695 2010-12-19 21:35 xmlbeans-2.3.0.jar
-rw-r--r-- 1 root root   225616 2010-12-19 21:35 xsdlib-20060615.jar
```

> It looks like they added LD_LIBRARY_PATH=/usr/lib/jni to their profile. That might work.
I don't know how to do it. I searched through 
[http://ubuntuforums.org/showthread.php?t=1523333&highlight=nevernote&page=2](http://ubuntuforums.org/showthread.php?t=1523333&highlight=nevernote&page=2)
and haven't found anything like that.

---

### Post by baumgarr on 2011-02-15
I don't see anything obviously wrong and other people using Mint haven't seen this (or haven't reported it anyway).  The LD_LIBRARY_PATH can be setup in multiple places, but the most common is /etc/profile.  There should already be one there.  If you are unfamiliar on editing this file, you're probably better off leaving it alone.  Every time you login this file is executed, so you really don't want to mess it up.

You can try uninstalling the deb and downloading the tar.gz file.  Once it is downloaded, just run the install script.  It does the exact same thing as the deb.  Alternatively, you can just download it and execute it directly.  The only reason this may work is in case the file somehow was corrupt.

One more question.  How much memory does the PC have?

---

### Post by arapaho on 2011-02-15
I have 2GB RAM.
It looks like I don't have QT Jambi Binary, but I'm not sure what to download precisely  from [http://qt.nokia.com/downloads](http://qt.nokia.com/downloads)
Can you refer me to specific file?

---

### Post by baumgarr on 2011-02-15
I can't find them on Nokia's web site any more.  They may have removed them.  You can try the ones at [https://sourceforge.net/projects/qtjambi/files/4.5.2/](https://sourceforge.net/projects/qtjambi/files/4.5.2/)

You shouldn't need to do this.  From my understanding the files you need are in the jar files already.

---

### Post by Perfect Storm on 2011-02-15
Please use the mint forum, thanks.
[http://forums.linuxmint.com/](http://forums.linuxmint.com/)


Thread closed.

---

