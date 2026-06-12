---
title: "firefox crash ABORT: X_CreatePixmap: BadAlloc"
date: 2011-10-21
forum: General Help
---

### Post by klausenm on 2011-10-21
Hi,

since i upgraded to kubuntu 11.10 i face regular firefox crashes (among other ocasional errors in the window system). The error message is:

###!!! ABORT: X_CreatePixmap: BadAlloc (insufficient resources for
###!!! operation); 404 requests ago: file
###!!! /build/buildd/firefox-7.0.1+build1+nobinonly/build-tree/mozilla/toolkit/xre/nsX11ErrorHandler.cpp,
###!!! /line 199

how can i fix this?

---

### Post by Moja on 2011-10-27
I get the same thing in a number of apps, only large windows though - small stuff (xterm, pidgin, konsole, etc.) work fine.  I'm running 1920x1280.  Even when I try to tunnel a remote X app back to my machine from another server, I get the same resource errors.  I would be SO grateful if one of you brilliant folks could help me fix this thing!  Here are a ton of different examples:

xterm@dellxps:~$ thunderbird 
failed to create drawable
###!!! ABORT: X_CreatePixmap: BadDrawable (invalid Pixmap or Window parameter); 6 requests ago: file /build/buildd/thunderbird-7.0.1+build1+nobinonly/build-tree/mozilla/mozilla/toolkit/xre/nsX11ErrorHandler.cpp, line 199
###!!! ABORT: X_CreatePixmap: BadDrawable (invalid Pixmap or Window parameter); 6 requests ago: file /build/buildd/thunderbird-7.0.1+build1+nobinonly/build-tree/mozilla/mozilla/toolkit/xre/nsX11ErrorHandler.cpp, line 199
colinb@dellxps:~$ Gtk-Message: Failed to load module "canberra-gtk-module"

xterm@dellxps:~$ firefox 
failed to create drawable
QPixmap::handle(): Pixmap is not an X11 class pixmap
###!!! ABORT: X_CreatePixmap: BadAlloc (insufficient resources for operation); 2 requests ago: file /build/buildd/firefox-7.0.1+build1+nobinonly/build-tree/mozilla/toolkit/xre/nsX11ErrorHandler.cpp, line 199
###!!! ABORT: X_CreatePixmap: BadAlloc (insufficient resources for operation); 2 requests ago: file /build/buildd/firefox-7.0.1+build1+nobinonly/build-tree/mozilla/toolkit/xre/nsX11ErrorHandler.cpp, line 199

xterm@dellxps:~$ google-chrome 
[9654:9654:5757593797:ERROR:x11_util.cc(815)] X Error detected: serial 1352, error_code 11 (BadAll
oc (insufficient resources for operation)), request_code 53, minor_code 0 (X_CreatePixmap)
[9654:9654:5757594554:ERROR:x11_util.cc(815)] X Error detected: serial 1353, error_code 9 (BadDraw
able (invalid Pixmap or Window parameter)), request_code 148, minor_code 4 (RenderCreatePicture)
[9654:9654:5757594593:ERROR:x11_util.cc(815)] X Error detected: serial 1354, error_code 9 (BadDraw
able (invalid Pixmap or Window parameter)), request_code 55, minor_code 0 (X_CreateGC)
[9654:9654:5757594995:ERROR:x11_util.cc(815)] X Error detected: serial 1355, error_code 10 (BadAcc
ess (attempt to access private resource denied)), request_code 139, minor_code 1 (X_ShmAttach)
[9654:9654:5757597014:ERROR:x11_util.cc(815)] X Error detected: serial 1356, error_code 145 (BadSh
mSeg (invalid shared segment parameter)), request_code 139, minor_code 5 (X_ShmCreatePixmap)

xterm@dellxps:~$ soffice 
QPixmap::handle(): Pixmap is not an X11 class pixmap

xterm@dellxps:~$ muon-installer 
QPixmap::handle(): Pixmap is not an X11 class pixmap
QPixmap::handle(): Pixmap is not an X11 class pixmap
colinb@dellxps:~$ X Error: BadAccess (attempt to access private resource denied) 10
  Extension:    139 (MIT-SHM)
  Minor opcode: 1 (X_ShmAttach)
  Resource id:  0x149
X Error: BadShmSeg (invalid shared segment parameter) 145
  Extension:    139 (MIT-SHM)
  Minor opcode: 5 (X_ShmCreatePixmap)
  Resource id:  0x112
QPainter::begin: Paint device returned engine == 0, type: 2
QPainter::setCompositionMode: Painter not active
QPainter::end: Painter not active, aborted
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x5200019

*** BELOW IS A LAUNCH FROM A REMOTE CLIENT BRINGING THE DISPLAY BACK TO MY X-SERVER

xterm@dellxps:~$ ssh -X my.work.fedora.box konqueror
kbuildsycoca4 running...
konqueror(24650)/kdeui (kdelibs): Attempt to use QAction "google-chrome" with KXMLGUIFactory! 
konqueror(24650)/kdeui (kdelibs): Attempt to use QAction "mozilla-firefox" with KXMLGUIFactory! 
konqueror(24650)/kdeui (kdelibs): Attempt to use QAction "" with KXMLGUIFactory! 
QPainter::begin: Paint device returned engine == 0, type: 2
QPainter::setCompositionMode: Painter not active
QPainter::end: Painter not active, aborted
X Error: BadAlloc (insufficient resources for operation) 11
  Major opcode: 53 (X_CreatePixmap)
  Resource id:  0x112
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Extension:    148 (RENDER)
  Minor opcode: 4 (RenderCreatePicture)
  Resource id:  0x5600091
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 55 (X_CreateGC)
  Resource id:  0x5600091

---

