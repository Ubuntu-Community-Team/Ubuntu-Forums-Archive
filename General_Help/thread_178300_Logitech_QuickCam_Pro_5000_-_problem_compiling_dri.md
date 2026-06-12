---
title: "Logitech QuickCam Pro 5000 - problem compiling driver"
date: 2006-05-17
forum: General Help
---

### Post by chichikov on 2006-05-17
Hello,

I'm a newbie trying to get a Logitech QuickCam Pro 5000 to work under Breezy using the driver from [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/) but am running into a problem when I do a make:

Building USB Video Class driver...
make[1]: Entering directory `/lib/modules/2.6.12-10-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.12-10-386/build'
make: *** [uvcvideo] Error 2

Any help gratefully appreciated!

---

### Post by edm00se on 2006-05-17
I am also interested in getting the Linux UVC driver to work (with the Quickcam Fusion). If anyone has successfully installed and used it, please, help a brother out.

---

### Post by edm00se on 2006-05-17
I got it to work with my Quickcam Fusion in Dapper.

It looks like you'll want to make sure your kernel headers package is installed. I didn't have mine installed when I initially tried the make, it gave me an error earlier than yours, saying that the directory didn't exist.

In any case, you might be interested in [this thread]("http://www.ubuntuforums.org/showthread.php?p=1026862").

---

