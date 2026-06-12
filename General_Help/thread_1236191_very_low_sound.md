---
title: "very low sound"
date: 2009-08-10
forum: General Help
---

### Post by MistaMista on 2009-08-10
i turn my volume up and can barely hear...wat 2 do

---

### Post by nikhilbhardwaj on 2009-08-10
i assume you have alsa installed
use alsamixer or any mixer of your choice to increase your sound

---

### Post by Cortux on 2009-08-10
Or you could try upgrading the ALSA Mixer, I had the same issue and this worked perfectly for me. try it out. 
 
[http://monespaceperso.org/blog-en/20...tu-jaunty-904/](http://monespaceperso.org/blog-en/20...tu-jaunty-904/)
 
Also dont forget to go to System >  Preferences > Sound and try the different devices, it also made a difference.

---

### Post by arky on 2009-08-10
If you have a 5.1 channel capable audio card, then enable surround by editing /etc/pulse/daemon.conf file. 

uncomment the line and change it from '2' to '6'

 default-sample-channels = 6

---

### Post by arky on 2009-08-10
[http://webupd8.blogspot.com/2009/06/enable-surround-sound-in-ubuntu-linux.html](http://webupd8.blogspot.com/2009/06/enable-surround-sound-in-ubuntu-linux.html)

---

