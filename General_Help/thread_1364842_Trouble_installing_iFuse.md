---
title: "Trouble installing iFuse"
date: 2009-12-26
forum: General Help
---

### Post by DubiousKing on 2009-12-26
I just got an iPod Touch for Christmas and was excited about using it, then discovered Ubuntu 8.04 doesn't detect it as an iPod-type device (it says it's a camera, but doesn't let me access it other than asking to import photos). I found [iFuse]("http://matt.colyer.name/projects/iphone-linux/index.php?title=Main_Page") and have been working at getting it to run, but I've run into a problem. Here's the output I get:

```
$ make
make  all-recursive
make[1]: Entering directory `/home/samba/MattColyer-ifuse-424e003'
Making all in src
make[2]: Entering directory `/home/samba/MattColyer-ifuse-424e003/src'
gcc -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -D_FILE_OFFSET_BITS=64 -I/usr/include/fuse   -pthread -I/usr/local/include -I/usr/local/include/libusb-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2   -g -g -O2 -lglib-2.0   -pthread -lfuse -lrt -ldl   -pthread -L/usr/local/lib -liphone -lplist -lusbmuxd -lgthread-2.0 -lrt -lgnutls -ltasn1 -lxml2 -lusb-1.0 -lglib-2.0    -o mount.fuse.ifuse ifuse.o  
ifuse.o: In function `main':
/home/samba/MattColyer-ifuse-424e003/src/ifuse.c:594: undefined reference to `iphone_get_device'
collect2: ld returned 1 exit status
make[2]: *** [mount.fuse.ifuse] Error 1
make[2]: Leaving directory `/home/samba/MattColyer-ifuse-424e003/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/samba/MattColyer-ifuse-424e003'
make: *** [all] Error 2

```I went into the code and couldn't find **iphone_get_device** anywhere in the header files. Has anyone else run into this, and if so how did you solve it?

---

### Post by kayvortex on 2009-12-26
Looks like a linking error, so the issue is probably not that the code is not compiling, but that you are missing a relevant library. What steps did you follow and what commands did you enter?

---

### Post by DubiousKing on 2009-12-26
I ran the commands given in the included README file, though I couldn't run the last one because it stopped working at **make**
```
./autogen.sh
./configure
make
sudo make install
```Here's the first lines of code from **ifuse.c**, the main file being compiled, where it's including the libraries.
```
#define FUSE_USE_VERSION  26

#include <fuse.h>
#include <stdio.h>
#include <string.h>
#include <errno.h>
#include <fcntl.h>
#include <glib.h>
#include <unistd.h>
#include <stdint.h>
#include <stdlib.h>

typedef uint32_t uint32;        // this annoys me too

#include <libiphone/libiphone.h>
#include <libiphone/lockdown.h>
#include <libiphone/afc.h>
```**iphone_get_device** would most likely be located in one of those last three header files, but it's not in any of them. If I didn't have one of libraries, it would've told me well before it got into the meat of the code (I know this because it did just that a couple of times before I had all of the required libraries).

---

### Post by kayvortex on 2010-01-03
Really sorry about the (really) late reply.

What library/binary are you trying to compile? iFuse itself? I appreciate the fact that what I'm about to say is not really an answer, but you don't need to compile it from source: the repo [**http://ppa.launchpad.net/jonabeck/ppa/ubuntu**]("http://ppa.launchpad.net/jonabeck/ppa/ubuntu") should have an acceptable version.

Personally, I followed the instructions [**here**]("http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux-part-2/"), and only bothered compiling the libgpod library since the repo above had all the other packages of the necessary version (that is, I got ifuse, libiphone-dev, git-core, libtool, intltool, gtk-doc-tools, libsqlite3-dev from the repo -- which is all the packages I needed for a *make* to succeed).

Unless you know that this won't work, I'd suggest getting iFuse and the like from the above repo and only compile libgpod. Otherwise, if you tell me the version of the sources you got, I can try giving it a go myself and see what happens.

Also, note that the *autogen.sh* and *configure* may have missed out a dependency -- you never know. I'd suggest making sure that you have the necessary libs manually. You can check dependencies and whether a package is installed or not by typing:
```
aptitude show *put_package_here*
```
For example, for me, "aptitude show ifuse" gives:
[INDENT]Package: ifuse
New: yes
State: [COLOR="Red"]installed[/COLOR]
Automatically installed: no
Version: 0.9.4-1ubuntu3~k
Priority: extra
Section: utils
Maintainer: Jonathan Beck <jonabeck@gmail.com>
Uncompressed Size: 61.4k
Depends: [COLOR="Red"]libc6 (>= 2.3.4), libfuse2 (>= 2.6), libglib2.0-0 (>= 2.14.1),
libgnutls26 (>= 2.7.14-0), libiphone0, libplist0 (>= 0.16), libtasn1-3
(>= 1.6-0), libusb-1.0-0 (>= 2:1.0.3), libusbmux0 (>= 1.0.0-rc1),
libxml2 (>= 2.6.27)[/COLOR]
Description: FUSE module for iPhone.
 iFuse allows you to mount an iPhone or iPod Touch under Linux using the USB
 cable. You can view and edit the files similar to a normal USB disk drive.
 iFuse does not require "jailbreaking" or voiding your warranty and works
 without needing extra software installed on the phone (such as `ssh`).[/INDENT]

Edit: you'll need dev packages for some of these (apparently libfuse and libglib2.0).

---

