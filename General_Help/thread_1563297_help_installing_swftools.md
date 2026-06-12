---
title: "help installing swftools"
date: 2010-08-28
forum: General Help
---

### Post by frank204 on 2010-08-28
i downloaded swftools-0.9.1.tar.gz and was having problems installing it.i did the "make" and "make install" but it comes up with these errors when i run it:

root@cadogan-desktop:/home/cadogan/Desktop/1# make install
making install in m4...
cd m4;make install
make[1]: Entering directory `/home/cadogan/Desktop/1/m4'
make[1]: Nothing to be done for `install'.
make[1]: Leaving directory `/home/cadogan/Desktop/1/m4'
making install in lib...
cd lib;make install
make[1]: Entering directory `/home/cadogan/Desktop/1/lib'
make[1]: Nothing to be done for `install'.
make[1]: Leaving directory `/home/cadogan/Desktop/1/lib'
making install in lib/pdf...
cd lib/pdf;make install
make[1]: Entering directory `/home/cadogan/Desktop/1/lib/pdf'
make[1]: Nothing to be done for `install'.
make[1]: Leaving directory `/home/cadogan/Desktop/1/lib/pdf'
making install in lib...
cd lib;make install
make[1]: Entering directory `/home/cadogan/Desktop/1/lib'
make[1]: Nothing to be done for `install'.
make[1]: Leaving directory `/home/cadogan/Desktop/1/lib'
making install in lib/python...
cd lib/python;make install
make[1]: Entering directory `/home/cadogan/Desktop/1/lib/python'
make[1]: Nothing to be done for `install'.
make[1]: Leaving directory `/home/cadogan/Desktop/1/lib/python'
making install in lib/ruby...
cd src;make install
make[1]: Entering directory `/home/cadogan/Desktop/1/src'
/bin/bash ../mkinstalldirs /usr/local/bin
/bin/bash ../mkinstalldirs /usr/local/share/man/man1
make[1]: Leaving directory `/home/cadogan/Desktop/1/src'
making install in avi2swf...
cd avi2swf;make install
make[1]: Entering directory `/home/cadogan/Desktop/1/avi2swf'
make[1]: Nothing to be done for `install'.
make[1]: Leaving directory `/home/cadogan/Desktop/1/avi2swf'
making install in swfs...
cd swfs;make install
make[1]: Entering directory `/home/cadogan/Desktop/1/swfs'
/bin/bash ../mkinstalldirs /usr/local/share/swftools
/bin/bash ../mkinstalldirs /usr/local/share/swftools/swfs
/usr/bin/install -c -m 644 ./simple_viewer.swf /usr/local/share/swftools/swfs/simple_viewer.swf
/usr/bin/install: cannot stat `./simple_viewer.swf': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/cadogan/Desktop/1/swfs'
make: *** [install] Error 2
root@cadogan-desktop:/home/cadogan/Desktop/1#

i tried to install it from the package manager but couldnt find it in there.just wondering what i was doing wrong or how i can install it easier.thanks

---

### Post by skatinjj on 2010-08-28
> **frank204 said:**
> i downloaded swftools-0.9.1.tar.gz and was having problems installing it.i did the "make" and "make install" but it comes up with these errors when i run it:

root@cadogan-desktop:/home/cadogan/Desktop/1# make install
making install in m4...
cd m4;make install
make[1]: Entering directory `/home/cadogan/Desktop/1/m4'
make[1]: Nothing to be done for `install'.
make[1]: Leaving directory `/home/cadogan/Desktop/1/m4'
making install in lib...
cd lib;make install
make[1]: Entering directory `/home/cadogan/Desktop/1/lib'
make[1]: Nothing to be done for `install'.
make[1]: Leaving directory `/home/cadogan/Desktop/1/lib'
making install in lib/pdf...
cd lib/pdf;make install
make[1]: Entering directory `/home/cadogan/Desktop/1/lib/pdf'
make[1]: Nothing to be done for `install'.
make[1]: Leaving directory `/home/cadogan/Desktop/1/lib/pdf'
making install in lib...
cd lib;make install
make[1]: Entering directory `/home/cadogan/Desktop/1/lib'
make[1]: Nothing to be done for `install'.
make[1]: Leaving directory `/home/cadogan/Desktop/1/lib'
making install in lib/python...
cd lib/python;make install
make[1]: Entering directory `/home/cadogan/Desktop/1/lib/python'
make[1]: Nothing to be done for `install'.
make[1]: Leaving directory `/home/cadogan/Desktop/1/lib/python'
making install in lib/ruby...
cd src;make install
make[1]: Entering directory `/home/cadogan/Desktop/1/src'
/bin/bash ../mkinstalldirs /usr/local/bin
/bin/bash ../mkinstalldirs /usr/local/share/man/man1
make[1]: Leaving directory `/home/cadogan/Desktop/1/src'
making install in avi2swf...
cd avi2swf;make install
make[1]: Entering directory `/home/cadogan/Desktop/1/avi2swf'
make[1]: Nothing to be done for `install'.
make[1]: Leaving directory `/home/cadogan/Desktop/1/avi2swf'
making install in swfs...
cd swfs;make install
make[1]: Entering directory `/home/cadogan/Desktop/1/swfs'
/bin/bash ../mkinstalldirs /usr/local/share/swftools
/bin/bash ../mkinstalldirs /usr/local/share/swftools/swfs
/usr/bin/install -c -m 644 ./simple_viewer.swf /usr/local/share/swftools/swfs/simple_viewer.swf
/usr/bin/install: cannot stat `./simple_viewer.swf': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/cadogan/Desktop/1/swfs'
make: *** [install] Error 2
root@cadogan-desktop:/home/cadogan/Desktop/1#

i tried to install it from the package manager but couldnt find it in there.just wondering what i was doing wrong or how i can install it easier.thanks

[Here]("http://packages.ubuntu.com/karmic/i386/swftools/download"), much easier.

Just pick a mirror from your area and download the .deb package

---

### Post by frank204 on 2010-08-29
thanks,it worked.:D

---

### Post by joemar on 2011-05-21
whats the update on swftools? can some one help me? :(

---

