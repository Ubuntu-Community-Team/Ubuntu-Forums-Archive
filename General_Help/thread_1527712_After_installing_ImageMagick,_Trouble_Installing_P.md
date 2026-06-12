---
title: "After installing ImageMagick, Trouble Installing PerlMagick"
date: 2010-07-09
forum: General Help
---

### Post by rocheteau on 2010-07-09
Hi, 
I have just installed ImageMagick but when I tried to install PerlMagick it bombed horribly at the make stage giving out pages of error messages. It may have to do with a difficulty in specifying the LD_LIBRARY_PATH in a system-wide manner i.e. I used "export LD_LIBRARY_PATH=/usr/local/lib" which, of course, only works for the current session. Does anyone know a system-wide way to do this? Googling produced no confirmed way.

Details:
Ubuntu 10.04 LTS

ImageMagick Installation as follows:
Installation of ImageMagick package: downloaded from [ftp://ftp.imagemagick.org/pub/ImageMagick/ImageMagick.tar.gz](ftp://ftp.imagemagick.org/pub/ImageMagick/ImageMagick.tar.gz), tar xzvf, ./configure, make, make install.
Tested installation via "/usr/local/bin/convert logo: logo.gif" which failed via inability to find libMagickCore.so.4 and libMagickWand.so.4 libraries.
In /usr/local/bin:
        ldd convert     --> shows locations of linked libraries with the two above being unfound
        whereis libMagickCore.so.4      --> /usr/local/lib/libMagickCore.so.4
        whereis libMagickWand.so.4      --> /usr/local/lib/libMagickWand.so.4
        env |grep LD_LIBRARY_PATH       --> environment variable didn't exist
        export LD_LIBRARY_PATH=/usr/local/lib   --> only works in the current session i.e. caused the "/usr/local/bin/convert logo: logo.gif" test to work i.e. produced a correct logo image which I viewed with eog.

PerlMagick installation:
PerlMagick-6.59 downloaded, 
In the Makefile.PL file I added "-I/usr/local/lib/" to reflect the above information from the ImageMagick installation. As I said the make command generated a great deal of error messaging which I won't give here unless someone can suggest a subset of the messaging that I should provide.

Thanks in advance for any help!

---

### Post by Jan-E on 2010-08-26
I had the same problem with LD_LIBRARY_PATH on Centos 5.4 and solved the problem by adding a parameter to ./configure:

./configure LDFLAGS='-L/usr/local/lib -R/usr/local/lib'

More info:
[http://www.imagemagick.org/script/advanced-unix-installation.php]("http://www.imagemagick.org/script/advanced-unix-installation.php")

The same solution might work for Ubuntu.

---

