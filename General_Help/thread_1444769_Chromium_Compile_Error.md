---
title: "Chromium Compile Error"
date: 2010-04-01
forum: General Help
---

### Post by esya on 2010-04-01
I am trying to compile Chromium([http://chromium.sourceforge.net/](http://chromium.sourceforge.net/)) on Ubuntu 9.10.

And I am getting /usr/bin/ld: cannot find -lXi error.

I checked the dependencies and the program expecting the files in that path  -L/usr/X11R6/lib -lGLU -lGL -lXmu -lXi -lX11 

I don't have  /usr/X11R6 directory in my computer. I found X11 file under the /etc/X11 directory but i could not find the Xi anywhere.

I set up these
sudo apt-get install libxv-dev
sudo apt-get install libxi-dev
sudo apt-get install libxmu-dev

Could you please help me if you have any idea?

Regards...

---

