---
title: "gettext warning when I'm compiling"
date: 2011-11-24
forum: General Help
---

### Post by nethero on 2011-11-24
I'm trying to compile amule.  I run ./configure in the amule directory and I get this warning....


```
  **** General Libraries and Tools ****
  Should ccache support be enabled?                          no
  Libraries aMule will use to build:
                             wxWidgets             2.8.12 (gtk2,shared)
                             crypto++              5.6.0 (installed, in /usr)
                             libupnp               1.6.6
                             libintl               Not detected
                             zlib                  1.2.3.3


 *** Warnings during configuration ***

* You need to install GNU gettext/gettext-tools to compile aMule with i18n
  support.
```

I have gettext installed, I can see it is installed when I open synaptic.  What package am I missing?

---

### Post by lookyn on 2011-12-01
same problem. 
My configure options:
```
./configure --prefix=/home/myname/amule/bin --enable-debug --enable-optimize --with-denoise-level=3 --enable-upnp --enable-geoip --enable-nls --enable-amule-gui --enable-amule-daemon --enable-amulecmd --enable-webserver --enable-alcc --enable-alc --enable-cas --enable-wxcas --enable-mmap --with-wxdir=/home/myname/amule/wx/build
```output:
```
 **** aMule Core ****
  Prefix where aMule should be installed?                    /home/myname/amule/bin
  Should aMule be compiled with i18n support?                no
  Should aMule be compiled in debug mode?                    yes
  Should aMule be compiled with profiling?                   no
  Should aMule be compiled with optimizations?               yes
  Should aMule be compiled with UPnP support?                yes
  Should aMule be compiled with IP2country support?          yes
  Should aMule monolithic application be built?              yes
  Should aMule daemon version be built?                      yes
  Should aMule remote gui be built?                          yes
  Crypto++ library/headers style?                            installed
...
  **** General Libraries and Tools ****
  Should ccache support be enabled?                          no
  Libraries aMule will use to build:
                             wxWidgets             2.8.12 (gtk2,shared)
                             crypto++              5.6.1 (installed, in /usr)
                             libupnp               1.6.6
                             libintl               Not detected
                             libGeoIP              system
                             libpng                1.2.46
                             libgd                 2.0.36
                             zlib                  1.2.3.4


 *** Warnings during configuration ***

* You need to install GNU gettext/gettext-tools to compile aMule with i18n
  support.
```you can see: no i18n support , and "libintl" is not detected , how to fix it? Or, do these matter?

`dpkg -l | grep gettext` gives me :
```
ii  gettext                                0.18.1.1-3ubuntu1                          GNU Internationalization utilities
ii  gettext-base                            0.18.1.1-3ubuntu1                          GNU Internationalization  utilities for the base system
ii  liblocale-gettext-perl                  1.05-6build1                               Using libc functions for  internationalization in Perl
ii  po-debconf                              1.0.16+nmu1                                tool for managing templates  file translations with gettext
```So **gettext** has been installed.
Thank you!

---

### Post by nethero on 2011-12-12
I compiled anyway and amule seems to work.  I never was able to get this issue resolved.  One of my friends also has 10.04 and was able to compile the same version of amule without this error.  Unfortunately, I did not get list of the packages installed on his computer so comparisons are impossible.  I'll track this some more later if I have the time, but for now amule is up and working.  :)

---

### Post by neonigma on 2012-03-31
Install autopoint package.

---

