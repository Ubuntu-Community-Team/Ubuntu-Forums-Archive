---
title: "Wubi crashes Windows 7"
date: 2011-01-31
forum: General Help
---

### Post by Photobug on 2011-01-31
I am preparing to install Ubuntu server to run the server I am building.  Both the server and Ubuntu are new to me.  In preparation to this I installed Wubi on my Windows 7 laptop.  It installed nicely and works smoothly.  Unfortunately when I went back into W7 it has crashed 5 times in a row.  Sometimes I got 5 minutes into the running of windows.  The last time it crashed before I could even log in.

I am unable to determine what is going on as i can't get around in my Windows for very long.  Fortunately the Ubuntu side of my computer is still working well.

My W7 install is on a smaller partition (80GB).  Would the Wubi installed on this same partition and maybe crowding the W7 install?  Should I create another partition to install the Wubi onto or just install a Ubuntu on  a separate partition?

How should i go about troubleshooting this?

---

### Post by Frogs Hair on 2011-01-31
Try this thread , there may be something helpful.[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by mastablasta on 2011-01-31
i sure hope you don't intend to run server on a wubi install.
 
Wubi uses a virtualisation (creates a large file) within windows system. if the file gets corrupted, you could lose everything. not to meniton you are limited in size of the os.
 
if you plan to have a server i would suggest at least to read Ubuntu manual to learn about desktop, and a few basic command and differences betwen Linux and windows, dual boot etc.
 
Next stop will be site called linuxcommand.org that offers another free e-book so you can learn command line interface under which the server runs.
 
to play arround with a server and learn a bit a virtual WAMP or (even better) LAMP server is also an option.

---

