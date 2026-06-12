---
title: "Incompatible libpng version in application and library"
date: 2009-10-09
forum: General Help
---

### Post by yt_vinay on 2009-10-09
Hi all,

Im trying to install ImageMagick and RMagick on an Ubuntu Intrepid system. I followed the tutorial here for the most part of it [http://www.randycullom.com/chatterbox/archives/2006/12/installing_imag.html](http://www.randycullom.com/chatterbox/archives/2006/12/installing_imag.html).

ImageMagick compiled fine but im getting the following error when i try to convert a png file.

/usr/local/bin/convert logo: logo.png
convert: Incompatible libpng version in application and library `logo.png'.

I found this link which is on the same issue [http://www.imagemagick.org/discourse-server/viewtopic.php?f=1&t=6810&start=0](http://www.imagemagick.org/discourse-server/viewtopic.php?f=1&t=6810&start=0). 

I found out the following...

1. There are 2 folders libpng,libpng12 in /usr/include. Both contain two files - png.h and pngconf.h - and both are versions 1.2.27. The same files are also in /usr/include which carry version number 1.2.27.

2. png.h and pngconf.h also exist in /usr/local/include but these files carry version 1.0.6

3. This is the configure statement i used for Imagemagick

./configure --enable-lzw=yes --enable-shared=yes --disable-static --without-perl --with-modules --without-magick-plus-plus --with-gs-font-dir=/usr/local/share/ghostscript/fonts

How can I get ImageMagick to work correctly for png? Im sure you can see that im a beginner. Please explain as much as you can. 

Thanks! 
Vinay.

---

### Post by yt_vinay on 2009-10-09
Ok I got this fixed by doing the following..

1. from /usr/include, type - 
sudo mv png.h ../local/include 
and then 
sudo mv pngconf.h ../local/include. 
This basically replaced the files versioned 1.0.6 in /usr/local/include with the files versioned 1.2.27

2. from the ImageMagick 6.2.3 directory, run 
sudo make uninstall 
to uninstall IM. Then 
/configure --enable-lzw=yes --enable-shared=yes --disable-static --without-perl --with-modules --without-magick-plus-plus --with-gs-font-dir=/usr/local/share/ghostscript/fonts 
to configure IM the way I wanted, then 
make 
and then 
sudo make install.

That got the PNG working. I dont know what happened behind the scenes though, so if anyone can explain that, for the sake of understanding, it would be great!

---

