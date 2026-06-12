---
title: "wine libgnutls-dev not found"
date: 2009-07-11
forum: General Help
---

### Post by Gosujii-sama on 2009-07-11
While attempting to compile wine for warcraft3 I get the error:

checking for gnutls/gnutls.h... yes
configure: error: libgnutls development files not found, no schannel support.
This is an error since --with-gnutls was requested.

However I have libgnutls-dev installed and fully updated as shown bellow:

construct@Diabolic-Construct:~/wine-war3$ sudo apt-get install libgnutls-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgnutls-dev is already the newest version.<<<<
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

libgnutls-dev package file is:
libgnutls-dev_2.0.4-1ubuntu2.5_i386.deb
using: ubuntu hardy 8.04 i386 arch

This tells me that its fully updated and should have no issues while compiling wine in this manner. I've been fishing for an answer on this for a long time now. I haven't recived ANY replies as of yet of what may be wrong or fixes for it. Not even questions to further it... I really want to get this fixed as I've fully converted to ubuntu linux and haven't been able to use war3 since the 1.23 update a few months back. I really miss war3 and need answers of any kind suggestions ideas anything.
tell me im not insane and that there is a bug of somekind or something im missing.

---

### Post by SixalivE on 2009-08-16
I was just looking for a way to get around the same problem you are experiencing and I am in the middle of compiling Wine now after updating gnutls-dev. Go to the GNU.org and download anything above version 2.2 (I used 2.4.0). Hopefully that works for you.

---

