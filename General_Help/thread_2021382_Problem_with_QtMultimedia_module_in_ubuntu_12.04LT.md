---
title: "Problem with QtMultimedia module in ubuntu 12.04LTS"
date: 2012-07-09
forum: General Help
---

### Post by hesitux on 2012-07-09
I have some problems with the Qt4 QtMultimedia module in ubuntu 12.04. I can't find its development files in /usr/include/qt4. Should i install extra packages for this? if yes , what is its name?

Note : I have installed QtSDK from ubuntu packages , not the SDK provided by Nokia.

---

### Post by Lukhaz on 2012-07-27
I have the same problem: no libqt4-multimedia nor libqt4-multimedia-dev package in ubuntu repositories

---

### Post by Strelz on 2012-08-04
I had the same problem and I solved it by downloading the QtSDK from Nokia.  It includes QtMultimedia.  You could copy this folder into usr/includes/Qt4, but I found that unnecessary as I have been using QtCreator (installed by Synaptic, its in an Ubuntu repository), and it found the folder even though it had installed in a branch off my home directory.

To use it, I just have to write:
 
#include <QtMultimedia/QtMultimedia> 

which gives me the entire package.

You must add QT += multimedia to the QtCreator pro file in order to link to the multimedia library.

I still have a question, however.  Why was it not included in the Ubuntu repository version?  Is there something wrong with it?  Will it be deprecated and replaced by something ele?  I could of course write directly to the alsa library, but that takes somewhat more work.  So, what is currently the best recommended way to access the alsa library?

---

