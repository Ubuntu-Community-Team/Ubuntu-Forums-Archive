---
title: "Screwed up my x server"
date: 2009-07-11
forum: General Help
---

### Post by Daremo_06 on 2009-07-11
janunty x64

Alright i was playing around with trying to get google earth to run and one of the links i found said to change libcrypto.so.0.9.8 to a .bak file.

Did that, earth then worked.. did a few other things, then i w about to log off and i double clicked on the user icon (drop down for swapping accounts, logging off, restart ect ect)  the system started to reboot (that normal? i have always gone to the menu selection in the drop down to reboot..)

Anyways after reboot, im coming up in terminal.  Try to startx and i get

/usr/bin/x11/x: error while loading shared libraries: libcrypto.so.0.9.8: cannot open shared object file: no such file or directory.
giving up.
xinit: no such file or directory (errno 2): unable to connect to x server
xinit: no such process (errno 3): server error
xauth: error in locking authority file name /home/rob/.xauthority

So I tried the apt-get reconfigure command for xserver that i found in another link here, then tried reinstalling the entire x-server package

still no luck.

Soooo what did I screw up and how do i get my desktop back? :)

ps i did a few other small things here and there, like a typo when I was typing chmod -x to the libcryp before getting google earth to work I accidentally typed sudo chmod -s.  I googled chmod -s and i didnt seem to find anything ... not sure that it matters?

Thanks!

---

