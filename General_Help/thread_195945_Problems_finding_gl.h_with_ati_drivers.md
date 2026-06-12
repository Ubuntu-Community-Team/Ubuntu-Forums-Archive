---
title: "Problems finding gl.h with ati drivers"
date: 2006-06-13
forum: General Help
---

### Post by zer0s on 2006-06-13
This is it, i'm having problems with the gl.h header after i've installed the ati drivers for the dapper drake.
My card is a X700 mobility with 256M.

It's a qt3 project and this is the exit when i try to do a make:

```
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I../material/vig/include -I/usr/include/qt3 -o main.o main.cpp
En el fitxer inclòs dès de glwidget.h:17,
                 dès de main.cpp:3:
/usr/include/qt3/qgl.h:79:20: error: GL/gl.h: El fitxer o directori no existeix
/usr/include/GL/glu.h:280: error: &#8216;GLint&#8217; does not name a type
/usr/include/GL/glu.h:281: error: &#8216;GLint&#8217; does not name a type
...

```

And this is my .pro file:

```
TEMPLATE	= app
LANGUAGE	= C++

CONFIG	+= qt thread warn_on release

LIBS	+= -lGL -lGLU -L/home/zer0s/graphic/lib -l3ds

INCLUDEPATH	+= /home/zer0s/graphic/include

HEADERS	+= glwidget.h \
	punt.h \
	vectorvig.h \
	InfoVehicle.h \
	textField.h \
	sliderText.h \
	boto.h

SOURCES	+= main.cpp \
	glwidget.cpp \
	punt.cpp \
	vectorvig.cpp \
	textField.cpp \
	sliderText.cpp \
	boto.cpp

FORMS	= vista_model.ui \
	finestraajuda.ui \
	EditorLlums.ui

```

Someone see the problem?

---

### Post by arng on 2006-10-13
Having a similar issue.

On the broader perspective I was on Kubuntu Breezy 5.10 MythTV 0.18.1 and wanted to upgrade to the latest MythTV.
Found that a few people installed 0.19 and 0.20 on dapper 6.06, so following that, upgraded to dapper.  It was not smooth, but not lost the system or seen other horrible scenarios others reported on major [k]ubuntu upgrades.  Needed to re-install the nvidia 5500 (dapper process is way better) and recompile ivtv with the new os.  Also need to fix the write access on the blog I am hosting.  Myth also lost a few functions, but that I don’t care about since I am aiming to re-install latest anyways, and even my db + recorded programs don’t matter too much right now.  Have not lost any recordings or anything in the database.

So Edgy Eft 6.10 seems to have the packages and save all the hassle.  But there are just user complains online that packages should be added to stable releases or dapper in our case.  And people seem to be looking for backporting to the existing systems, which appear missing.  Fully agree with those points.
So I could choose between going with 6.10 beta and the packaged Myth, compile myth on 6.06, or switch altogether to FC5 on which myth packaging seems most stable and active.  The first try was to compile from sources since I have successfully compiled 0.19 on Breezy before, and it did not seem too much hassle.  Unfortunately on 6.06 and 0.20 this process was not work on first pass.

Ideas / suggestions / solutions would be very welcomed.

I got that similar issue while trying to compile mythtv 0.20 on dapper from svn per [http://www.mythtv.org/wiki/index.php/Installing_MythTV_SVN_on_Ubuntu_Breezy#How_do_I_compile_the_source_code.3F](http://www.mythtv.org/wiki/index.php/Installing_MythTV_SVN_on_Ubuntu_Breezy#How_do_I_compile_the_source_code.3F).
Added multiverse to an base dapper sources file and then apt-get installed all prerequisites.
Took the stable branch:
```
svn co http://svn.mythtv.org/svn/branches/release-0-20-fixes/mythtv

```Then did:
```
./configure --prefix=/usr/local
make

```And go that error.

I could not find the file anywhere either:
```
$ find / -iname gl.h
$
```

The missing inclusion is at:
```
$ grep GL/gl.h /usr/include/qt3/qgl.h
# include <OpenGL/gl.h>
# include <GL/gl.h>
$
```

The full compile error is:

```
make[2]: Leaving directory `/usr/src/mythtv/release-0-20-fixes/mythtv/libs/libmythtv'
cd libmythui && qmake libmythui.pro -o Makefile
cd libmythui && make -f Makefile
make[2]: Entering directory `/usr/src/mythtv/release-0-20-fixes/mythtv/libs/libmythui'
g++ -c -pipe -march=pentiumpro -I/usr/include/kde/artsc -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -Wall -W -g -D_REENTRANT -DPIC -fPIC  -DMMX -Di386 -DUSING_FREEBOX -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -DPREFIX=\"/usr/local\" -DLIBDIR=\"/usr/local/lib\" -DUSE_OPENGL_PAINTER -DUSE_JOYSTICK_MENU -DUSE_LIRC -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I../../../../../../local/include -I../../../../../../X11R6/include -I../libmyth -I../.. -I.. -I../../../../../../include/qt3 -o mythmainwindow.o mythmainwindow.cpp
In file included from ../libmythui/mythmainwindow.h:9,
                 from ../libmyth/mythdialogs.h:48,
                 from ../libmyth/lirc.h:9,
                 from mythmainwindow.cpp:19:
../../../../../../include/qt3/qgl.h:79:20: error: GL/gl.h: No such file or directory
/usr/include/GL/glu.h:280: error: &#1490;GLint&#1490; does not name a type
/usr/include/GL/glu.h:281: error: &#1490;GLint&#1490; does not name a type
/usr/include/GL/glu.h:282: error: &#1490;GLint&#1490; does not name a type
/usr/include/GL/glu.h:283: error: &#1490;GLint&#1490; does not name a type
/usr/include/GL/glu.h:284: error: &#1490;GLint&#1490; does not name a type
/usr/include/GL/glu.h:285: error: &#1490;GLint&#1490; does not name a type
/usr/include/GL/glu.h:286: error: &#1490;GLboolean&#1490; does not name a type
/usr/include/GL/glu.h:287: error: &#1490;GLdouble&#1490; has not been declared
/usr/include/GL/glu.h:287: error: &#1490;GLdouble&#1490; has not been declared
/usr/include/GL/glu.h:287: error: &#1490;GLdouble&#1490; has not been declared
/usr/include/GL/glu.h:287: error: &#1490;GLint&#1490; has not been declared
/usr/include/GL/glu.h:287: error: &#1490;GLint&#1490; has not been declared
/usr/include/GL/glu.h:291: error: &#1490;GLdouble&#1490; has not been declared
/usr/include/GL/glu.h:291: error: &#1490;GLdouble&#1490; has not been declared
/usr/include/GL/glu.h:291: error: &#1490;GLint&#1490; has not been declared
/usr/include/GL/glu.h:291: error: &#1490;GLint&#1490; has not been declared
/usr/include/GL/glu.h:296: error: expected initializer before &#1490;*&#1490; token
/usr/include/GL/glu.h:297: error: &#1490;GLenum&#1490; has not been declared
/usr/include/GL/glu.h:297: error: &#1490;GLfloat&#1490; has not been declared
/usr/include/GL/glu.h:298: error: expected initializer before &#1490;*&#1490; token
/usr/include/GL/glu.h:299: error: &#1490;GLenum&#1490; has not been declared
/usr/include/GL/glu.h:299: error: &#1490;GLdouble&#1490; has not been declared
/usr/include/GL/glu.h:300: error: expected &#1490;,&#1490; or &#1490;...&#1490; before &#1490;*&#1490; token
/usr/include/GL/glu.h:301: error: variable or field &#1490;gluLookAt&#1490; declared void
/usr/include/GL/glu.h:301: error: &#1490;GLdouble&#1490; was not declared in this scope
/usr/include/GL/glu.h:301: error: &#1490;GLdouble&#1490; was not declared in this scope
/usr/include/GL/glu.h:301: error: &#1490;GLdouble&#1490; was not declared in this scope
/usr/include/GL/glu.h:301: error: &#1490;GLdouble&#1490; was not declared in this scope
/usr/include/GL/glu.h:301: error: &#1490;GLdouble&#1490; was not declared in this scope
/usr/include/GL/glu.h:301: error: &#1490;GLdouble&#1490; was not declared in this scope
/usr/include/GL/glu.h:301: error: &#1490;GLdouble&#1490; was not declared in this scope
/usr/include/GL/glu.h:301: error: &#1490;GLdouble&#1490; was not declared in this scope
/usr/include/GL/glu.h:301: error: &#1490;GLdouble&#1490; was not declared in this scope
/usr/include/GL/glu.h:301: error: initializer expression list treated as compound expression
/usr/include/GL/glu.h:305: error: &#1490;GLenum&#1490; has not been declared
/usr/include/GL/glu.h:306: error: &#1490;GLenum&#1490; has not been declared
/usr/include/GL/glu.h:307: error: &#1490;GLvoid&#1490; has not been declared
/usr/include/GL/glu.h:308: error: &#1490;GLvoid&#1490; has not been declared
/usr/include/GL/glu.h:309: error: &#1490;GLint&#1490; has not been declared
/usr/include/GL/glu.h:309: error: &#1490;GLfloat&#1490; has not been declared
/usr/include/GL/glu.h:309: error: &#1490;GLint&#1490; has not been declared
/usr/include/GL/glu.h:309: error: &#1490;GLfloat&#1490; has not been declared
/usr/include/GL/glu.h:309: error: &#1490;GLint&#1490; has not been declared
/usr/include/GL/glu.h:309: error: &#1490;GLenum&#1490; has not been declared
/usr/include/GL/glu.h:310: error: &#1490;GLenum&#1490; has not been declared
/usr/include/GL/glu.h:310: error: &#1490;GLfloat&#1490; has not been declared
/usr/include/GL/glu.h:311: error: &#1490;GLint&#1490; has not been declared
/usr/include/GL/glu.h:311: error: &#1490;GLfloat&#1490; has not been declared
/usr/include/GL/glu.h:311: error: &#1490;GLint&#1490; has not been declared
/usr/include/GL/glu.h:311: error: &#1490;GLfloat&#1490; has not been declared
/usr/include/GL/glu.h:311: error: &#1490;GLint&#1490; has not been declared
/usr/include/GL/glu.h:311: error: &#1490;GLint&#1490; has not been declared
/usr/include/GL/glu.h:311: error: &#1490;GLfloat&#1490; has not been declared
/usr/include/GL/glu.h:311: error: &#1490;GLint&#1490; has not been declared
/usr/include/GL/glu.h:311: error: &#1490;GLint&#1490; has not been declared
/usr/include/GL/glu.h:311: error: &#1490;GLenum&#1490; has not been declared
/usr/include/GL/glu.h:312: error: variable or field &#1490;gluOrtho2D&#1490; declared void
/usr/include/GL/glu.h:312: error: &#1490;GLdouble&#1490; was not declared in this scope
/usr/include/GL/glu.h:312: error: &#1490;GLdouble&#1490; was not declared in this scope
/usr/include/GL/glu.h:312: error: &#1490;GLdouble&#1490; was not declared in this scope
/usr/include/GL/glu.h:312: error: &#1490;GLdouble&#1490; was not declared in this scope
/usr/include/GL/glu.h:312: error: initializer expression list treated as compound expression
/usr/include/GL/glu.h:313: error: &#1490;GLdouble&#1490; has not been declared
/usr/include/GL/glu.h:313: error: &#1490;GLdouble&#1490; has not been declared
/usr/include/GL/glu.h:313: error: &#1490;GLint&#1490; has not been declared
/usr/include/GL/glu.h:313: error: &#1490;GLint&#1490; has not been declared
/usr/include/GL/glu.h:313: error: &#1490;GLdouble&#1490; has not been declared
/usr/include/GL/glu.h:313: error: &#1490;GLdouble&#1490; has not been declared
/usr/include/GL/glu.h:314: error: variable or field &#1490;gluPerspective&#1490; declared void
/usr/include/GL/glu.h:314: error: &#1490;GLdouble&#1490; was not declared in this scope
/usr/include/GL/glu.h:314: error: &#1490;GLdouble&#1490; was not declared in this scope
/usr/include/GL/glu.h:314: error: &#1490;GLdouble&#1490; was not declared in this scope
/usr/include/GL/glu.h:314: error: &#1490;GLdouble&#1490; was not declared in this scope
/usr/include/GL/glu.h:314: error: initializer expression list treated as compound expression
/usr/include/GL/glu.h:315: error: variable or field &#1490;gluPickMatrix&#1490; declared void
/usr/include/GL/glu.h:315: error: &#1490;GLdouble&#1490; was not declared in this scope
/usr/include/GL/glu.h:315: error: &#1490;GLdouble&#1490; was not declared in this scope
/usr/include/GL/glu.h:315: error: &#1490;GLdouble&#1490; was not declared in this scope
/usr/include/GL/glu.h:315: error: &#1490;GLdouble&#1490; was not declared in this scope
/usr/include/GL/glu.h:315: error: &#1490;GLint&#1490; was not declared in this scope
/usr/include/GL/glu.h:315: error: &#1490;viewport&#1490; was not declared in this scope
/usr/include/GL/glu.h:315: error: initializer expression list treated as compound expression
/usr/include/GL/glu.h:316: error: &#1490;GLint&#1490; does not name a type
/usr/include/GL/glu.h:317: error: &#1490;GLint&#1490; has not been declared
/usr/include/GL/glu.h:317: error: &#1490;GLfloat&#1490; has not been declared
/usr/include/GL/glu.h:317: error: &#1490;GLint&#1490; has not been declared
/usr/include/GL/glu.h:317: error: &#1490;GLenum&#1490; has not been declared
/usr/include/GL/glu.h:318: error: &#1490;GLenum&#1490; has not been declared
/usr/include/GL/glu.h:319: error: &#1490;GLenum&#1490; has not been declared
/usr/include/GL/glu.h:320: error: &#1490;GLenum&#1490; has not been declared
/usr/include/GL/glu.h:321: error: &#1490;GLenum&#1490; has not been declared
/usr/include/GL/glu.h:322: error: &#1490;GLboolean&#1490; has not been declared
/usr/include/GL/glu.h:323: error: &#1490;GLint&#1490; does not name a type
/usr/include/GL/glu.h:324: error: &#1490;GLdouble&#1490; has not been declared
/usr/include/GL/glu.h:324: error: &#1490;GLint&#1490; has not been declared
/usr/include/GL/glu.h:324: error: &#1490;GLint&#1490; has not been declared
/usr/include/GL/glu.h:326: error: &#1490;GLvoid&#1490; has not been declared
/usr/include/GL/glu.h:327: error: &#1490;GLenum&#1490; has not been declared
/usr/include/GL/glu.h:330: error: &#1490;GLdouble&#1490; has not been declared
/usr/include/GL/glu.h:330: error: &#1490;GLdouble&#1490; has not been declared
/usr/include/GL/glu.h:330: error: &#1490;GLdouble&#1490; has not been declared
/usr/include/GL/glu.h:331: error: &#1490;GLenum&#1490; has not been declared
/usr/include/GL/glu.h:331: error: &#1490;GLdouble&#1490; has not been declared
/usr/include/GL/glu.h:332: error: &#1490;GLdouble&#1490; has not been declared
/usr/include/GL/glu.h:332: error: &#1490;GLvoid&#1490; has not been declared
/usr/include/GL/glu.h:333: error: &#1490;GLint&#1490; does not name a type
/usr/include/GL/glu.h:334: error: &#1490;GLint&#1490; does not name a type
../../../../../../include/qt3/qsqldatabase.h:63: warning: &#1490;class QSqlDriverCreatorBase&#1490; has virtual functions but non-virtual destructor
make[2]: *** [mythmainwindow.o] Error 1
make[2]: Leaving directory `/usr/src/mythtv/release-0-20-fixes/mythtv/libs/libmythui'
make[1]: *** [sub-libmythui] Error 2
make[1]: Leaving directory `/usr/src/mythtv/release-0-20-fixes/mythtv/libs'
make: *** [sub-libs] Error 2

```

---

### Post by arng on 2006-10-13
Ok, I see that the latest 0.20 .deb files are in the multiverse.

And that edgy has 0.20 [http://packages.ubuntu.com/edgy/graphics/mythtv](http://packages.ubuntu.com/edgy/graphics/mythtv) while dapper only has 0.18.1 [http://packages.ubuntu.com/dapper/graphics/mythtv](http://packages.ubuntu.com/dapper/graphics/mythtv).

Is there any obvious incompatibility I am missing here, or would just installing all the below .deb files get me to mythtv 0.20 on dapper 6.06 on a relatively simple and safe way?

```

lynx --dump "http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mythtv/?C=M;O=D" | egrep "http.*0.20-0.2.*(all|i386).*deb"
  13. http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mythtv/mythtv-frontend_0.20-0.2ubuntu1_i386.deb
  14. http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mythtv/mythtv-backend_0.20-0.2ubuntu1_i386.deb
  15. http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mythtv/libmyth-0.20_0.20-0.2ubuntu1_i386.deb
  16. http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mythtv/libmyth-0.20-dev_0.20-0.2ubuntu1_i386.deb
  17. http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mythtv/mythtv_0.20-0.2ubuntu1_all.deb
  18. http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mythtv/mythtv-common_0.20-0.2ubuntu1_all.deb
  19. http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mythtv/mythtv-doc_0.20-0.2ubuntu1_all.deb
  20. http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mythtv/mythtv-database_0.20-0.2ubuntu1_all.deb

lynx --dump "http://archive.ubuntu.com/ubuntu/pool/multiverse/m/myththemes/?C=M;O=D" | egrep "http.*0.20-0.1.*(all|i386).*deb"
   5. http://archive.ubuntu.com/ubuntu/pool/multiverse/m/myththemes/mythtv-themes_0.20-0.1_all.deb

lynx --dump "http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mythplugins/?C=M;O=D" | egrep "http.*0.20-0.6.*(all|i386).*deb"
  17. http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mythplugins/mythweather_0.20-0.6ubuntu3_i386.deb
  18. http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mythplugins/mythvideo_0.20-0.6ubuntu3_i386.deb
  19. http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mythplugins/mythphone_0.20-0.6ubuntu3_i386.deb
  20. http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mythplugins/mythnews_0.20-0.6ubuntu3_i386.deb
  21. http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mythplugins/mythmusic_0.20-0.6ubuntu3_i386.deb
  22. http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mythplugins/mythgame_0.20-0.6ubuntu3_i386.deb
  23. http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mythplugins/mythgallery_0.20-0.6ubuntu3_i386.deb
  24. http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mythplugins/mythflix_0.20-0.6ubuntu3_i386.deb
  25. http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mythplugins/mythdvd_0.20-0.6ubuntu3_i386.deb
  27. http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mythplugins/mythcontrols_0.20-0.6ubuntu3_i386.deb
  29. http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mythplugins/mythbrowser_0.20-0.6ubuntu3_i386.deb
  31. http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mythplugins/mytharchive_0.20-0.6ubuntu3_i386.deb
  33. http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mythplugins/mythweb_0.20-0.6ubuntu3_all.deb
  36. http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mythplugins/mythplugins_0.20-0.6ubuntu3_all.deb
  43. http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mythplugins/mytharchive-data_0.20-0.6ubuntu3_all.deb

```

---

### Post by arng on 2006-10-13
Not an official release, but hey anything apt-get away is better, and this one worked for me:

[http://digg.com/linux_unix/MythTV_version_0_20_released#c3029825](http://digg.com/linux_unix/MythTV_version_0_20_released#c3029825)

---

