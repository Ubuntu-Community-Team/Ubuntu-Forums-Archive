---
title: "New Ereader software for Ubuntu on ereader.com"
date: 2010-03-12
forum: General Help
---

### Post by cfastner on 2010-03-12
Has anyone tried the new Ubuntu version of Ereader software beta on "ereader.com"?  I have been running the Windows version of this software in wine for awhile and that seems to work but a version specifically for Ubuntu would be GREAT!

It has a completely different interface from the Windows version (with fewer options for configuring) but it appears that I can download books right from ereader.com (with the windows version I had to download the books and put them in the proper folder that the ereader software looked for its library).

I have been trying to figure out WHERE the Ubuntu software puts the downloaded ebooks (because I have several other books that I would like to try in the program and they were NOT downloaded from ereader.com).

Anyone have any comments?

Charlie
  ~~~

---

### Post by radu_radu on 2010-03-16
Hello,
I just found the ereader software, too. I've forced its install on 64-bit Karmic, and although it starts, it won't work because it asks for libqsqlite.so - _32bit_. If I add it to /usr/lib32, it still won't see it, regardless if I add it with its full path from the .deb: /usr/lib**32**/qt4/plugins/sqldrivers/, or if I just dump it in /usr/lib32/ directly.
So i guess the question is: how to install libqsqlite.so 32-bit on a 64-bit system?
Here's ereader from console:
```
$ /usr/bin/ereader
QSqlDatabase: QSQLITE driver not loaded
QSqlDatabase: available drivers:
QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
Object::connect: No such slot ReaderLibraryOnlineSubpane::downloadErrorSlot (int, DownloadErrorType, QString) in reader-library-online-subpane.cc:113
Object::connect: No such signal ReaderLibraryLocalSubpane::openBook (QString) in reader-library-pane.cc:36
QSqlQuery::prepare: database not open
QSqlDatabasePrivate::removeDatabase: connection 'qt_sql_default_connection' is still in use, all queries will cease to work.
```
Here's what ereader links against:
```
$ ldd /usr/bin/ereader
        linux-gate.so.1 =>  (0xf7735000)
        libQtXml.so.4 => /usr/lib32/libQtXml.so.4 (0xf76ba000)
        libQtNetwork.so.4 => /usr/lib32/libQtNetwork.so.4 (0xf75a4000)
        libQtSql.so.4 => /lib32/libQtSql.so.4 (0xf7566000)
        libQtGui.so.4 => /usr/lib32/libQtGui.so.4 (0xf6bc8000)
        libQtCore.so.4 => /usr/lib32/libQtCore.so.4 (0xf6995000)
        libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf68a3000)
        libm.so.6 => /lib32/libm.so.6 (0xf687d000)
        libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf685e000)
        libc.so.6 => /lib32/libc.so.6 (0xf6719000)
        libz.so.1 => /usr/lib32/libz.so.1 (0xf6703000)
        libpthread.so.0 => /lib32/libpthread.so.0 (0xf66ea000)
        libaudio.so.2 => /usr/lib32/libaudio.so.2 (0xf66d0000)
        libpng12.so.0 => /usr/lib32/libpng12.so.0 (0xf66a8000)
        libfreetype.so.6 => /usr/lib32/libfreetype.so.6 (0xf6628000)
        libgobject-2.0.so.0 => /usr/lib32/libgobject-2.0.so.0 (0xf65ea000)
        libSM.so.6 => /usr/lib32/libSM.so.6 (0xf65e1000)
        libICE.so.6 => /usr/lib32/libICE.so.6 (0xf65c6000)
        libglib-2.0.so.0 => /lib32/libglib-2.0.so.0 (0xf6510000)
        libXrender.so.1 => /usr/lib32/libXrender.so.1 (0xf6506000)
        libfontconfig.so.1 => /usr/lib32/libfontconfig.so.1 (0xf64d8000)
        libXext.so.6 => /usr/lib32/libXext.so.6 (0xf64c8000)
        libX11.so.6 => /usr/lib32/libX11.so.6 (0xf6399000)
        libgthread-2.0.so.0 => /usr/lib32/libgthread-2.0.so.0 (0xf6393000)
        librt.so.1 => /lib32/librt.so.1 (0xf638a000)
        libdl.so.2 => /lib32/libdl.so.2 (0xf6385000)
        /lib/ld-linux.so.2 (0xf7736000)
        libXt.so.6 => /usr/lib32/libXt.so.6 (0xf6332000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0xf632e000)
        libpcre.so.3 => /lib32/libpcre.so.3 (0xf62fd000)
        libuuid.so.1 => /lib32/libuuid.so.1 (0xf62f8000)
        libexpat.so.1 => /lib32/libexpat.so.1 (0xf62d0000)
        libxcb.so.1 => /usr/lib32/libxcb.so.1 (0xf62b2000)
        libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf62ad000)

```

---

### Post by StuartN on 2010-03-16
> **cfastner said:**
> Anyone have any comments?

Calibre has a completely open architecture and it is possible to feed ereader books into it, even with DRM [http://www.mobileread.mobi/forums/showthread.php?t=50513](http://www.mobileread.mobi/forums/showthread.php?t=50513)

---

### Post by pirron on 2010-03-17
I installed ereader for ubuntu (32-bit version) but it stalls after I put my username and password. This is the message that appears at the console


No such slot ReaderLibraryOnlineSubpane::downloadErrorSlot (int, DownloadErrorType, QString) in reader-library-online-subpane.cc:113
Object::connect: No such signal ReaderLibraryLocalSubpane::openBook (QString) in reader-library-pane.cc:36

---

### Post by perryrt on 2010-04-02
+1 - I have the exact same error message (well, besides the smiley...)

Additional background in my case - Running 9.10 on a Dell laptop (Inspiron 1420). I put in my account information the first time, and now every time I start it up, I can see my library/bookshelf starting to load from the internet.... after 30 sec or so, the window dims and ... nada.

Is there anything else I can provide to help troubleshoot this?

---

### Post by frncz on 2010-04-21
Do try calibre. I find it installs easily, with a good interface and copes with many formats and transfers to many reader devices.

---

### Post by perryrt on 2010-05-07
[QUOTE="frncz"]Do try calibre. I find it installs easily, with a good interface and copes with many formats and transfers to many reader devices.[/QUOTE]

I agree and have used Calibre in the past...but what about DRM? I opened up my copy here and can't get it to open an eReader DRM'ed (password protected) book.

Supposedly the eReader software can do that. If the blinking thing would work.

Without getting into a philosophical argument here, I have no issues with DRM per se, but I DO object when it bars legitimate use like this.

Anyone had any more luck with this?

---

