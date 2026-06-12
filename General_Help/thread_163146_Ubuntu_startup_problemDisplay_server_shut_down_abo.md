---
title: "Ubuntu startup problem:Display server shut down about 6 times in the last 90 seconds."
date: 2006-04-20
forum: General Help
---

### Post by blindjedi on 2006-04-20
Hi Everyone,

 I seem to be getting this message during startup. 
"The display server has been shut down about 6 times in the last 90 seconds. It is likely that something bad is going on. Waiting for 2 minutes before trying again"

Once I say 'OK', ubunut takes me to the login prompt. After 2 minutes, it tries to start the display server againg and the same message reappears.

Any suggestions ? I am working on a compaq presario laptop and do not remember doing anything to the gnome settings before my last shutdown.

Thanks,
Shyam

---

### Post by gondilon on 2006-04-20
you could try two things. First, try running sudo dpkg-reconfigure xserver-xorg
from a text console. If that  does not work, boot into windows and get the free program offered at this url :[http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm) that will allow you to edit your linux partition from windows.  After installing, open /etc/x11/xorg.conf . scroll down until you find the section that identifies your graphics card.  Add option "noaccel" at the end of the section, save the file, and restart ubuntu.

---

### Post by blindjedi on 2006-04-28
Hi, Thanks for the suggestions. I tried working them out. It seems like both the options would not help. I think I might be doing something wrong while reconfiguring xserver. I used the defaults that were chosen during the xserver reconfiguration.

---

