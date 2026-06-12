---
title: "How to get Kbasic to work...."
date: 2011-09-07
forum: General Help
---

### Post by tonwib on 2011-09-07
Hello group.

I am running Ubuntu 11.04 (32-bit) on my laptop and I want to install Kbasic.

I've downloaded the tar.gz file, but nothing happens when I click on 'kbide'.

After some reading on the net I found out that there are some dependecies:
- linux-gate.so.1
- libQtWebKit.so.4 ? /usr/lib/libQtWebKit.so.4
- libphonon.so.4 ? /usr/lib/libphonon.so.4
- libQtSql.so.4 ? /usr/lib/libQtSql.so.4
- libQtGui.so.4 ? /usr/lib/libQtGui.so.4
- libpng12.so.0 ? /usr/lib/libpng12.so.0
- libSM.so.6 ? /usr/lib/libSM.so.6
- libICE.so.6 ? /usr/lib/libICE.so.6
- libXi.so.6 ? /usr/lib/libXi.so.6
- libXrender.so.1 ? /usr/lib/libXrender.so.1
- libXrandr.so.2 ? /usr/lib/libXrandr.so.2
- libXfixes.so.3 ? /usr/lib/libXfixes.so.3
- libXcursor.so.1 ? /usr/lib/libXcursor.so.1
- libXinerama.so.1 ? /usr/lib/libXinerama.so.1
- libfreetype.so.6 ? /usr/lib/libfreetype.so.6
- libfontconfig.so.1 ? /usr/lib/libfontconfig.so.1
- libXext.so.6 ? /usr/lib/libXext.so.6
- libX11.so.6 ? /usr/lib/libX11.so.6
- libQtNetwork.so.4 ? /usr/lib/libQtNetwork.so.4
- libQtCore.so.4 ? /usr/lib/libQtCore.so.4
- libz.so.1 ? /lib/libz.so.1
- librt.so.1 ? /lib/librt.so.1
- libdl.so.2 ? /lib/libdl.so.2
- libpthread.so.0 ? /lib/libpthread.so.0
- libstdc++.so.6 ? /usr/lib/libstdc++.so.6
- libm.so.6 ? /lib/libm.so.6
- libgcc_s.so.1 ? /lib/libgcc_s.so.1
- libc.so.6 ? /lib/libc.so.6
- libQtDBus.so.4 ? /usr/lib/libQtDBus.so.4
- libexpat.so.1 ? /lib/libexpat.so.1
- libXau.so.6 ? /usr/lib/libXau.so.6
- libxcb-xlib.so.0 ? /usr/lib/libxcb-xlib.so.0
- libxcb.so.1 ? /usr/lib/libxcb.so.1
- /lib/ld-linux.so.2
- libdbus-1.so.3 ? /lib/libdbus-1.so.3
- libQtXml.so.4 ? /usr/lib/libQtXml.so.4

I am missing some of these files from which I think are essential for Kbasic.
Also, I am stuck because the synaptic package manager _doesn't_ offer me to install some of these necessary files.

After some more reading I found suggestions that I should install the whole Qt4 package from Nokia, which I did. But, the result remains the same: nothing happens.

Does any of you have a guideline on how to install all the libs mentioned above and a proper way of installing Kbasic on Ubuntu 11.04?

Appreciate your help.

Ton Wibier

---

### Post by zero2xiii on 2011-09-07
Hay,

Normaly a ziped file should be uncompressed, then adjusted to your system, the installed.

Normaly the procedure will be something of this sort:

In terminal.
CD to extracted folder
make (or ./make)
make install


This is as far as I can remember how most applications that are in source form installed.

Good luck though

---

