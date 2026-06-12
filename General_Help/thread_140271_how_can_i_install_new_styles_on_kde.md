---
title: "how can i install new styles on kde"
date: 2006-03-05
forum: General Help
---

### Post by bdb51 on 2006-03-05
Can anyone show me how to install new styles on kde

---

### Post by BiTRIDER on 2006-03-05
Try this...

Download the style file you like from [www.kde-look.org](www.kde-look.org), extract it to some folder then look for a script (typically style-install.sh). Run that script in konsole (e.g. ./style-install.sh) and you should find the new style available in the System-Settings > Appearance > Styles

---

### Post by chavo on 2006-03-05
KDE or QT styles are actually plugins and they need to be compiled. If you can't find a deb then you need to compile it. 
Compiling kde-styles is easy, you just need to get a compiler and some basic development files.

sudo apt-get install build-essential
sudo apt-get build-dep kdebase

Those two commands should get you a working environment.
Now decompress the archive and cd into the new directory.
Now run this ->

./configure --prefix /usr
make
sudo make install

The procedure is the same for kwin decorations.

---

### Post by Kernel Sanders on 2006-03-06
The only thing that annoys me about KDE is the clock! Its so annoying!

Any way of just themeing that?

John

---

