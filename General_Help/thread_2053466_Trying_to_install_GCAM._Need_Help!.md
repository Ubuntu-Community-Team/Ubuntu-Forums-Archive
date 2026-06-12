---
title: "Trying to install GCAM. Need Help!"
date: 2012-09-05
forum: General Help
---

### Post by 777funk on 2012-09-05
I've been trying to install PyCAM, heekscnc, and GCAM (software for creating G-Code for a CNC Machine) and getting nowhere with it. 

This page assumes that the user knows how to install something in Ubuntu. I don't know enough to have a clue. Where would I start for installing this:
[http://gcam.js.cx/wiki/Main_Page](http://gcam.js.cx/wiki/Main_Page)

---

### Post by oldos2er on 2012-09-05
There's a deb file, [http://gcam.js.cx/files/gcam_2008.03.08_i386.deb](http://gcam.js.cx/files/gcam_2008.03.08_i386.deb)
But since it's fairly old I'm thinking it may not install properly. Only way is to try it.

---

### Post by sanderj on 2012-09-05
Compiling from source is time consuming and not easy. Here's how it workes for me on Ubuntu 12.04 for gcam:

```

sudo apt-get install libgtk2.0-dev
sudo apt-get install libgtkglext1-dev


wget http://gcam.js.cx/files/gcam-2010.07.27.tar.gz
tar xvzf gcam-2010.07.27.tar.gz 
cd gcam-2010.07.27/
./configure
make
sudo make install

```

If you have Ubuntu 12.04 64-bit, I can create a .deb for you.

---

### Post by 777funk on 2012-09-05
Thanks! Got it installed. I had to adjust a little here and there to get the right folders. But worked great. Thanks!

The software was a little disappointing. Seems like I can't import a drawing. Not sure how to use it without an existing dxf etc. And the documentation doesn't really explain as far as I can see either.

So since all my CAD is in DXF, I guess I'll have to keep looking or just stick with Windows if my search comes up empty.

---

