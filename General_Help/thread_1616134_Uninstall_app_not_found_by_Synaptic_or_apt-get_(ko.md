---
title: "Uninstall app not found by Synaptic or apt-get? (kobo-desktop)"
date: 2010-11-07
forum: General Help
---

### Post by forteller on 2010-11-07
I don't know how, but on my 64 bit machine I installed this 32 bit deb file: [kobo-desktop.deb]("http://dl.dropbox.com/u/2183775/kobo-desktop.deb"). I did that while using Ubuntu 10.04. Now I've updated to 10.10, and I can't uninstall it. Searching for "kobo" in Synaptic or USC only gives me a game, and using apt-get I get this error (I've included some output from the last command I run so you can see that my system does recognize that kobo-desktop is ins fact installed):

Errors were encountered while processing:
 linux-image-2.6.35-23-generic
 linux-image-generic
 kobo-desktop
 linux-image
[I]yyy@xxx:~$ sudo apt-get purge kobo-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package kobo-desktop
[/I]

Any help would be very much appreciated!

---

### Post by Barriehie on 2010-11-07
> **forteller said:**
> I don't know how, but on my 64 bit machine I installed this 32 bit deb file: [kobo-desktop.deb]("http://dl.dropbox.com/u/2183775/kobo-desktop.deb"). I did that while using Ubuntu 10.04. Now I've updated to 10.10, and I can't uninstall it. Searching for "kobo" in Synaptic or USC only gives me a game, and using apt-get I get this error (I've included some output from the last command I run so you can see that my system does recognize that kobo-desktop is ins fact installed):

Errors were encountered while processing:
 linux-image-2.6.35-23-generic
 linux-image-generic
 kobo-desktop
 linux-image
[I]yyy@xxx:~$ sudo apt-get purge kobo-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package kobo-desktop
[/I]

Any help would be very much appreciated!

Have a look in /var/cache/apt/archives and see if you can find the original .deb file you installed from; won't be there if you dl'ed it from outside the repos unless you put it there.  If you've got that you can reinstall via gdebi-gtk and then everything should be in place to purge or remove the package.

---

### Post by forteller on 2010-11-08
> **Barriehie said:**
> Have a look in /var/cache/apt/archives and see if you can find the original .deb file you installed from; won't be there if you dl'ed it from outside the repos unless you put it there.  If you've got that you can reinstall via gdebi-gtk and then everything should be in place to purge or remove the package.

The .deb was not in /var/cache/apt/archives. I downloaded the .deb file from the link I gave above (it's the same version as the one I have installed) and tried to install that, but I only got this error message:

```
$ sudo dpkg -i --force-architecture ./kobo-desktop.deb 
[sudo] password for xxx: 
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 194922 files and directories currently installed.)
Preparing to replace kobo-desktop 1.4-1 (using ./kobo-desktop.deb) ...
Unpacking replacement kobo-desktop ...
dpkg: dependency problems prevent configuration of kobo-desktop:
 kobo-desktop depends on libpng3; however:
  Package libpng3 is not installed.
dpkg: error processing kobo-desktop (--install):
 dependency problems - leaving unconfigured
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for python-support ...
Errors were encountered while processing:
 kobo-desktop
```

---

### Post by Barriehie on 2010-11-08
See if you've got kobo* in /var/lib/dpkg/info/ directory.

---

### Post by Barriehie on 2010-11-08
I've dl'ed the file and .deb's aren't hard to take apart.  It's just an ar file so:
```

ar -x <somefilename.deb>
``` will extract it.  I'll have a look at what it does where.  Work calls right now...

---

### Post by forteller on 2010-11-08
> **Barriehie said:**
> See if you've got kobo* in /var/lib/dpkg/info/ directory.
Yes, there's a file called kobo-desktop.list

> **Barriehie said:**
> I've dl'ed the file and .deb's aren't hard to take apart.  It's just an ar file so:
```

ar -x <somefilename.deb>
``` will extract it.  I'll have a look at what it does where.  Work calls right now...

Thank you!

---

### Post by Barriehie on 2010-11-08
> **forteller said:**
> Yes, there's a file called kobo-desktop.list



Thank you!

Okay, well since it won't install it so we can purge it we have option b...

So ```
ar -x kobo-desktop.deb
``` yielded the control.tar.gz and data.tar.gz files.  We're not interested in the control.tar.gz file; that contains the info you see in the package manager, or what's shown by aptitude.  So ```
gzip -d ./data.tar.gz && tar -xvvf ./data.tar 1>./kobofilez
``` yields:
```

drwxr-xr-x george/george     0 2010-10-26 08:00 ./
drwxr-xr-x george/george     0 2010-10-26 08:00 ./lib/
drwxr-xr-x george/george     0 2010-10-26 08:00 ./lib/udev/
drwxr-xr-x george/george     0 2010-10-26 08:00 ./lib/udev/rules.d/
-rw-r--r-- george/george    96 2010-10-26 08:00 ./lib/udev/rules.d/99-kobo.rules
drwxr-xr-x george/george     0 2010-10-26 08:00 ./usr/
drwxr-xr-x george/george     0 2010-10-26 08:00 ./usr/share/
drwxr-xr-x george/george     0 2010-10-26 08:00 ./usr/share/applications/
-rw-r--r-- george/george   145 2010-10-26 08:00 ./usr/share/applications/Kobo.desktop
drwxr-xr-x george/george     0 2010-10-26 08:00 ./usr/bin/
-rwxr-xr-x george/george    89 2010-10-26 08:00 ./usr/bin/Kobo
drwxr-xr-x george/george     0 2010-10-26 08:00 ./usr/local/
drwxr-xr-x george/george     0 2010-10-26 08:00 ./usr/local/Trolltech/
drwxr-xr-x george/george     0 2010-10-26 08:00 ./usr/local/Trolltech/Qt-4.6.2/
drwxr-xr-x george/george     0 2010-10-26 08:00 ./usr/local/Trolltech/Qt-4.6.2/lib/
-rwxr-xr-x george/george 277632 2010-10-26 08:00 ./usr/local/Trolltech/Qt-4.6.2/lib/libQtSvgKobo.so.4.6.2
-rwxr-xr-x george/george 9137896 2010-10-26 08:00 ./usr/local/Trolltech/Qt-4.6.2/lib/libQtGuiKobo.so.4.6.2
-rwxr-xr-x george/george  116840 2010-10-26 08:00 ./usr/local/Trolltech/Qt-4.6.2/lib/libQtTestKobo.so.4.6.2
-rwxr-xr-x george/george 2063832 2010-10-26 08:00 ./usr/local/Trolltech/Qt-4.6.2/lib/libQtScriptKobo.so.4.6.2
-rwxr-xr-x george/george 2229396 2010-10-26 08:00 ./usr/local/Trolltech/Qt-4.6.2/lib/libQtCoreKobo.so.4.6.2
-rwxr-xr-x george/george  215260 2010-10-26 08:00 ./usr/local/Trolltech/Qt-4.6.2/lib/libQtXmlKobo.so.4.6.2
-rwxr-xr-x george/george  652896 2010-10-26 08:00 ./usr/local/Trolltech/Qt-4.6.2/lib/libQtSqlKobo.so.4.6.2
-rwxr-xr-x george/george  951484 2010-10-26 08:00 ./usr/local/Trolltech/Qt-4.6.2/lib/libQtNetworkKobo.so.4.6.2
-rwxr-xr-x george/george 14050432 2010-10-26 08:00 ./usr/local/Trolltech/Qt-4.6.2/lib/libQtWebKitKobo.so.4.6.2
drwxr-xr-x george/george        0 2010-10-26 08:00 ./usr/local/Trolltech/Qt-4.6.2/plugins/
drwxr-xr-x george/george        0 2010-10-26 08:00 ./usr/local/Trolltech/Qt-4.6.2/plugins/imageformats/
-rwxr-xr-x george/george    13864 2010-10-26 08:00 ./usr/local/Trolltech/Qt-4.6.2/plugins/imageformats/libqsvg.so
-rwxr-xr-x george/george   337528 2010-10-26 08:00 ./usr/local/Trolltech/Qt-4.6.2/plugins/imageformats/libqmng.so
-rwxr-xr-x george/george    26208 2010-10-26 08:00 ./usr/local/Trolltech/Qt-4.6.2/plugins/imageformats/libqgif.so
-rwxr-xr-x george/george    22140 2010-10-26 08:00 ./usr/local/Trolltech/Qt-4.6.2/plugins/imageformats/libqico.so
-rwxr-xr-x george/george   329960 2010-10-26 08:00 ./usr/local/Trolltech/Qt-4.6.2/plugins/imageformats/libqtiff.so
-rwxr-xr-x george/george   149196 2010-10-26 08:00 ./usr/local/Trolltech/Qt-4.6.2/plugins/imageformats/libqjpeg.so
drwxr-xr-x george/george        0 2010-10-26 08:00 ./usr/local/Kobo/
-rwxr-xr-x george/george    49966 2010-10-26 08:00 ./usr/local/Kobo/libQtSolutions_SingleApplication-2.6.so.1.0.0
-rwxr-xr-x george/george 12104359 2010-10-26 07:57 ./usr/local/Kobo/libnickel.so.1.0.0
drwxr-xr-x george/george        0 2010-10-26 08:00 ./usr/local/Kobo/images/
-rw-r--r-- george/george     2271 2010-06-04 11:39 ./usr/local/Kobo/images/C3EI9ubvokyGlLUq-wDU9Q - bbMediumGridList.parsed
-rw-r--r-- george/george     3381 2010-06-04 11:39 ./usr/local/Kobo/images/Uct4FLUivUyRsFAYkxvTgg - bbMediumGridList.parsed
-rw-r--r-- george/george     2043 2010-06-04 11:39 ./usr/local/Kobo/images/f7_AF2Y7rU6x0JcdzuYifA - bbMediumGridList.parsed
-rw-r--r-- george/george     3392 2010-07-03 12:18 ./usr/local/Kobo/images/2HNtp-7RuEWetxHwRQ3n3g - iPhoneThumbnail.parsed
-rw-r--r-- george/george    20098 2010-06-04 11:39 ./usr/local/Kobo/images/Vsdoxk3ZjEOf4xgMizJbMQ - NickelBookCover.parsed
-rw-r--r-- george/george     2715 2010-06-04 11:39 ./usr/local/Kobo/images/2HNtp-7RuEWetxHwRQ3n3g - bbMediumGridList.parsed
-rw-r--r-- george/george    26512 2010-06-04 11:39 ./usr/local/Kobo/images/f7_AF2Y7rU6x0JcdzuYifA - NickelBookCover.parsed
-rw-r--r-- george/george     2916 2010-07-03 12:18 ./usr/local/Kobo/images/C3EI9ubvokyGlLUq-wDU9Q - iPhoneThumbnail.parsed
-rw-r--r-- george/george     1911 2010-07-03 12:20 ./usr/local/Kobo/images/Vsdoxk3ZjEOf4xgMizJbMQ - iPhoneThumbnail.parsed
-rw-r--r-- george/george     4352 2010-07-03 12:19 ./usr/local/Kobo/images/Uct4FLUivUyRsFAYkxvTgg - iPhoneThumbnail.parsed
-rw-r--r-- george/george    54445 2010-06-04 11:39 ./usr/local/Kobo/images/Uct4FLUivUyRsFAYkxvTgg - NickelBookCover.parsed
-rw-r--r-- george/george    47650 2010-06-04 11:39 ./usr/local/Kobo/images/2HNtp-7RuEWetxHwRQ3n3g - NickelBookCover.parsed
-rw-r--r-- george/george     2378 2010-07-03 12:19 ./usr/local/Kobo/images/f7_AF2Y7rU6x0JcdzuYifA - iPhoneThumbnail.parsed
-rw-r--r-- george/george    35232 2010-06-04 11:39 ./usr/local/Kobo/images/C3EI9ubvokyGlLUq-wDU9Q - NickelBookCover.parsed
-rw-r--r-- george/george     1591 2010-06-04 11:39 ./usr/local/Kobo/images/Vsdoxk3ZjEOf4xgMizJbMQ - bbMediumGridList.parsed
-rw-r--r-- george/george    19765 2010-10-26 08:00 ./usr/local/Kobo/Kobo.png
-rwxr-xr-x george/george  1243043 2010-10-26 08:00 ./usr/local/Kobo/libqca.so
-rwxr-xr-x george/george    23690 2010-10-26 08:00 ./usr/local/Kobo/libQtSolutions_IOCompressor-2.3.so.1.0.0
-rw-r--r-- george/george  4376576 2010-10-26 08:00 ./usr/local/Kobo/Kobo.sqlite
drwxr-xr-x george/george        0 2010-10-26 08:00 ./usr/local/Kobo/crypto/
-rwxr-xr-x george/george   365121 2010-10-26 08:00 ./usr/local/Kobo/crypto/libqca-ossl.so
-rwxr-xr-x george/george  4337299 2010-10-26 08:00 ./usr/local/Kobo/Kobo
-rw-r--r-- george/george      437 2010-10-26 07:51 ./usr/local/Kobo/libnickel.prl
lrwxrwxrwx george/george        0 2010-10-26 08:00 ./usr/local/Trolltech/Qt-4.6.2/lib/libQtScriptKobo.so -> libQtScriptKobo.so.4.6.2
lrwxrwxrwx george/george        0 2010-10-26 08:00 ./usr/local/Trolltech/Qt-4.6.2/lib/libQtCoreKobo.so.4 -> libQtCoreKobo.so.4.6.2
lrwxrwxrwx george/george        0 2010-10-26 08:00 ./usr/local/Trolltech/Qt-4.6.2/lib/libQtCoreKobo.so.4.6 -> libQtCoreKobo.so.4.6.2
lrwxrwxrwx george/george        0 2010-10-26 08:00 ./usr/local/Trolltech/Qt-4.6.2/lib/libQtNetworkKobo.so -> libQtNetworkKobo.so.4.6.2
lrwxrwxrwx george/george        0 2010-10-26 08:00 ./usr/local/Trolltech/Qt-4.6.2/lib/libQtNetworkKobo.so.4 -> libQtNetworkKobo.so.4.6.2
lrwxrwxrwx george/george        0 2010-10-26 08:00 ./usr/local/Trolltech/Qt-4.6.2/lib/libQtSqlKobo.so.4 -> libQtSqlKobo.so.4.6.2
lrwxrwxrwx george/george        0 2010-10-26 08:00 ./usr/local/Trolltech/Qt-4.6.2/lib/libQtScriptKobo.so.4 -> libQtScriptKobo.so.4.6.2
lrwxrwxrwx george/george        0 2010-10-26 08:00 ./usr/local/Trolltech/Qt-4.6.2/lib/libQtSqlKobo.so -> libQtSqlKobo.so.4.6.2
lrwxrwxrwx george/george        0 2010-10-26 08:00 ./usr/local/Trolltech/Qt-4.6.2/lib/libQtSvgKobo.so -> libQtSvgKobo.so.4.6.2
lrwxrwxrwx george/george        0 2010-10-26 08:00 ./usr/local/Trolltech/Qt-4.6.2/lib/libQtGuiKobo.so -> libQtGuiKobo.so.4.6.2
lrwxrwxrwx george/george        0 2010-10-26 08:00 ./usr/local/Trolltech/Qt-4.6.2/lib/libQtCoreKobo.so -> libQtCoreKobo.so.4.6.2
lrwxrwxrwx george/george        0 2010-10-26 08:00 ./usr/local/Trolltech/Qt-4.6.2/lib/libQtSqlKobo.so.4.6 -> libQtSqlKobo.so.4.6.2
lrwxrwxrwx george/george        0 2010-10-26 08:00 ./usr/local/Trolltech/Qt-4.6.2/lib/libQtXmlKobo.so -> libQtXmlKobo.so.4.6.2
lrwxrwxrwx george/george        0 2010-10-26 08:00 ./usr/local/Trolltech/Qt-4.6.2/lib/libQtTestKobo.so.4.6 -> libQtTestKobo.so.4.6.2
lrwxrwxrwx george/george        0 2010-10-26 08:00 ./usr/local/Trolltech/Qt-4.6.2/lib/libQtGuiKobo.so.4.6 -> libQtGuiKobo.so.4.6.2
lrwxrwxrwx george/george        0 2010-10-26 08:00 ./usr/local/Trolltech/Qt-4.6.2/lib/libQtTestKobo.so.4 -> libQtTestKobo.so.4.6.2
lrwxrwxrwx george/george        0 2010-10-26 08:00 ./usr/local/Trolltech/Qt-4.6.2/lib/libQtNetworkKobo.so.4.6 -> libQtNetworkKobo.so.4.6.2
lrwxrwxrwx george/george        0 2010-10-26 08:00 ./usr/local/Trolltech/Qt-4.6.2/lib/libQtWebKitKobo.so -> libQtWebKitKobo.so.4.6.2
lrwxrwxrwx george/george        0 2010-10-26 08:00 ./usr/local/Trolltech/Qt-4.6.2/lib/libQtWebKitKobo.so.4 -> libQtWebKitKobo.so.4.6.2
lrwxrwxrwx george/george        0 2010-10-26 08:00 ./usr/local/Trolltech/Qt-4.6.2/lib/libQtWebKitKobo.so.4.6 -> libQtWebKitKobo.so.4.6.2
lrwxrwxrwx george/george        0 2010-10-26 08:00 ./usr/local/Trolltech/Qt-4.6.2/lib/libQtSvgKobo.so.4.6 -> libQtSvgKobo.so.4.6.2
lrwxrwxrwx george/george        0 2010-10-26 08:00 ./usr/local/Trolltech/Qt-4.6.2/lib/libQtGuiKobo.so.4 -> libQtGuiKobo.so.4.6.2
lrwxrwxrwx george/george        0 2010-10-26 08:00 ./usr/local/Trolltech/Qt-4.6.2/lib/libQtScriptKobo.so.4.6 -> libQtScriptKobo.so.4.6.2
lrwxrwxrwx george/george        0 2010-10-26 08:00 ./usr/local/Trolltech/Qt-4.6.2/lib/libQtXmlKobo.so.4.6 -> libQtXmlKobo.so.4.6.2
lrwxrwxrwx george/george        0 2010-10-26 08:00 ./usr/local/Trolltech/Qt-4.6.2/lib/libQtTestKobo.so -> libQtTestKobo.so.4.6.2
lrwxrwxrwx george/george        0 2010-10-26 08:00 ./usr/local/Trolltech/Qt-4.6.2/lib/libQtSvgKobo.so.4 -> libQtSvgKobo.so.4.6.2
lrwxrwxrwx george/george        0 2010-10-26 08:00 ./usr/local/Trolltech/Qt-4.6.2/lib/libQtXmlKobo.so.4 -> libQtXmlKobo.so.4.6.2
lrwxrwxrwx george/george        0 2010-10-26 08:00 ./usr/local/Kobo/libQtSolutions_IOCompressor-2.3.so.1 -> libQtSolutions_IOCompressor-2.3.so.1.0.0
lrwxrwxrwx george/george        0 2010-10-26 07:57 ./usr/local/Kobo/libnickel.so -> libnickel.so.1.0.0
lrwxrwxrwx george/george        0 2010-10-26 07:57 ./usr/local/Kobo/libnickel.so.1 -> libnickel.so.1.0.0
lrwxrwxrwx george/george        0 2010-10-26 08:00 ./usr/local/Kobo/libQtSolutions_SingleApplication-2.6.so.1 -> libQtSolutions_SingleApplication-2.6.so.1.0.0
lrwxrwxrwx george/george        0 2010-10-26 08:00 ./usr/local/Kobo/libQtSolutions_SingleApplication-2.6.so -> libQtSolutions_SingleApplication-2.6.so.1.0.0
lrwxrwxrwx george/george        0 2010-10-26 08:00 ./usr/local/Kobo/libQtSolutions_IOCompressor-2.3.so -> libQtSolutions_IOCompressor-2.3.so.1.0.0
lrwxrwxrwx george/george        0 2010-10-26 07:57 ./usr/local/Kobo/libnickel.so.1.0 -> libnickel.so.1.0.0
lrwxrwxrwx george/george        0 2010-10-26 08:00 ./usr/local/Kobo/libQtSolutions_SingleApplication-2.6.so.1.0 -> libQtSolutions_SingleApplication-2.6.so.1.0.0
lrwxrwxrwx george/george        0 2010-10-26 08:00 ./usr/local/Kobo/libQtSolutions_IOCompressor-2.3.so.1.0 -> libQtSolutions_IOCompressor-2.3.so.1.0.0

``` 

Running that through gawk I come up with:

```

/
/lib/
/lib/udev/
/lib/udev/rules.d/
/lib/udev/rules.d/99-kobo.rules
/usr/
/usr/share/
/usr/share/applications/
/usr/share/applications/Kobo.desktop
/usr/bin/
/usr/bin/Kobo
/usr/local/
/usr/local/Trolltech/
/usr/local/Trolltech/Qt-4.6.2/
/usr/local/Trolltech/Qt-4.6.2/lib/
/usr/local/Trolltech/Qt-4.6.2/lib/libQtSvgKobo.so.4.6.2
/usr/local/Trolltech/Qt-4.6.2/lib/libQtGuiKobo.so.4.6.2
/usr/local/Trolltech/Qt-4.6.2/lib/libQtTestKobo.so.4.6.2
/usr/local/Trolltech/Qt-4.6.2/lib/libQtScriptKobo.so.4.6.2
/usr/local/Trolltech/Qt-4.6.2/lib/libQtCoreKobo.so.4.6.2
/usr/local/Trolltech/Qt-4.6.2/lib/libQtXmlKobo.so.4.6.2
/usr/local/Trolltech/Qt-4.6.2/lib/libQtSqlKobo.so.4.6.2
/usr/local/Trolltech/Qt-4.6.2/lib/libQtNetworkKobo.so.4.6.2
/usr/local/Trolltech/Qt-4.6.2/lib/libQtWebKitKobo.so.4.6.2
/usr/local/Trolltech/Qt-4.6.2/plugins/
/usr/local/Trolltech/Qt-4.6.2/plugins/imageformats/
/usr/local/Trolltech/Qt-4.6.2/plugins/imageformats/libqsvg.so
/usr/local/Trolltech/Qt-4.6.2/plugins/imageformats/libqmng.so
/usr/local/Trolltech/Qt-4.6.2/plugins/imageformats/libqgif.so
/usr/local/Trolltech/Qt-4.6.2/plugins/imageformats/libqico.so
/usr/local/Trolltech/Qt-4.6.2/plugins/imageformats/libqtiff.so
/usr/local/Trolltech/Qt-4.6.2/plugins/imageformats/libqjpeg.so
/usr/local/Kobo/
/usr/local/Kobo/libQtSolutions_SingleApplication-2.6.so.1.0.0
/usr/local/Kobo/libnickel.so.1.0.0
/usr/local/Kobo/images/
/usr/local/Kobo/images/C3EI9ubvokyGlLUq-wDU9Q
/usr/local/Kobo/images/Uct4FLUivUyRsFAYkxvTgg
/usr/local/Kobo/images/f7_AF2Y7rU6x0JcdzuYifA
/usr/local/Kobo/images/2HNtp-7RuEWetxHwRQ3n3g
/usr/local/Kobo/images/Vsdoxk3ZjEOf4xgMizJbMQ
/usr/local/Kobo/images/2HNtp-7RuEWetxHwRQ3n3g
/usr/local/Kobo/images/f7_AF2Y7rU6x0JcdzuYifA
/usr/local/Kobo/images/C3EI9ubvokyGlLUq-wDU9Q
/usr/local/Kobo/images/Vsdoxk3ZjEOf4xgMizJbMQ
/usr/local/Kobo/images/Uct4FLUivUyRsFAYkxvTgg
/usr/local/Kobo/images/Uct4FLUivUyRsFAYkxvTgg
/usr/local/Kobo/images/2HNtp-7RuEWetxHwRQ3n3g
/usr/local/Kobo/images/f7_AF2Y7rU6x0JcdzuYifA
/usr/local/Kobo/images/C3EI9ubvokyGlLUq-wDU9Q
/usr/local/Kobo/images/Vsdoxk3ZjEOf4xgMizJbMQ
/usr/local/Kobo/Kobo.png
/usr/local/Kobo/libqca.so
/usr/local/Kobo/libQtSolutions_IOCompressor-2.3.so.1.0.0
/usr/local/Kobo/Kobo.sqlite
/usr/local/Kobo/crypto/
/usr/local/Kobo/crypto/libqca-ossl.so
/usr/local/Kobo/Kobo
/usr/local/Kobo/libnickel.prl
/usr/local/Trolltech/Qt-4.6.2/lib/libQtScriptKobo.so
/usr/local/Trolltech/Qt-4.6.2/lib/libQtCoreKobo.so.4
/usr/local/Trolltech/Qt-4.6.2/lib/libQtCoreKobo.so.4.6
/usr/local/Trolltech/Qt-4.6.2/lib/libQtNetworkKobo.so
/usr/local/Trolltech/Qt-4.6.2/lib/libQtNetworkKobo.so.4
/usr/local/Trolltech/Qt-4.6.2/lib/libQtSqlKobo.so.4
/usr/local/Trolltech/Qt-4.6.2/lib/libQtScriptKobo.so.4
/usr/local/Trolltech/Qt-4.6.2/lib/libQtSqlKobo.so
/usr/local/Trolltech/Qt-4.6.2/lib/libQtSvgKobo.so
/usr/local/Trolltech/Qt-4.6.2/lib/libQtGuiKobo.so
/usr/local/Trolltech/Qt-4.6.2/lib/libQtCoreKobo.so
/usr/local/Trolltech/Qt-4.6.2/lib/libQtSqlKobo.so.4.6
/usr/local/Trolltech/Qt-4.6.2/lib/libQtXmlKobo.so
/usr/local/Trolltech/Qt-4.6.2/lib/libQtTestKobo.so.4.6
/usr/local/Trolltech/Qt-4.6.2/lib/libQtGuiKobo.so.4.6
/usr/local/Trolltech/Qt-4.6.2/lib/libQtTestKobo.so.4
/usr/local/Trolltech/Qt-4.6.2/lib/libQtNetworkKobo.so.4.6
/usr/local/Trolltech/Qt-4.6.2/lib/libQtWebKitKobo.so
/usr/local/Trolltech/Qt-4.6.2/lib/libQtWebKitKobo.so.4
/usr/local/Trolltech/Qt-4.6.2/lib/libQtWebKitKobo.so.4.6
/usr/local/Trolltech/Qt-4.6.2/lib/libQtSvgKobo.so.4.6
/usr/local/Trolltech/Qt-4.6.2/lib/libQtGuiKobo.so.4
/usr/local/Trolltech/Qt-4.6.2/lib/libQtScriptKobo.so.4.6
/usr/local/Trolltech/Qt-4.6.2/lib/libQtXmlKobo.so.4.6
/usr/local/Trolltech/Qt-4.6.2/lib/libQtTestKobo.so
/usr/local/Trolltech/Qt-4.6.2/lib/libQtSvgKobo.so.4
/usr/local/Trolltech/Qt-4.6.2/lib/libQtXmlKobo.so.4
/usr/local/Kobo/libQtSolutions_IOCompressor-2.3.so.1
/usr/local/Kobo/libnickel.so
/usr/local/Kobo/libnickel.so.1
/usr/local/Kobo/libQtSolutions_SingleApplication-2.6.so.1
/usr/local/Kobo/libQtSolutions_SingleApplication-2.6.so
/usr/local/Kobo/libQtSolutions_IOCompressor-2.3.so
/usr/local/Kobo/libnickel.so.1.0
/usr/local/Kobo/libQtSolutions_SingleApplication-2.6.so.1.0
/usr/local/Kobo/libQtSolutions_IOCompressor-2.3.so.1.0

```

I'ld advise against installing anything not in the repos.  There can be dire consequences!  Not so much this time but what if there were hundreds of line items that were extracted, all over the place, pulling in dependencies!!!!  :(

---

### Post by Barriehie on 2010-11-08
Could always retry your original attempt at installing it AFTER installing libpng3, and then purge kobo-desktop.

Let us know what works.  I had to do the uninstall thing like I've outlined for you here to uninstall limewire.

Barrie

---

### Post by Barriehie on 2010-11-08
forteller, did you follow the post with the .deb file?

---

### Post by forteller on 2010-11-10
Hey, sorry for my late reply. I've been busy, but I'm very thankful for your help!

> **Barriehie said:**
> Could always retry your original attempt at installing it AFTER installing libpng3, and then purge kobo-desktop.

Let us know what works.  I had to do the uninstall thing like I've outlined for you here to uninstall limewire.

Barrie

I installed libpng3, and yes, then I was able to install kobo-desktop.deb. But running apt-get purge kobo-desktop still gives me:

```
$ sudo apt-get purge kobo-desktop 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package kobo-desktop
```

---

