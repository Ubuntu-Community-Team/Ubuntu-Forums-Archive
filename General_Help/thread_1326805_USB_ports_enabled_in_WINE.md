---
title: "USB ports enabled in WINE?"
date: 2009-11-14
forum: General Help
---

### Post by dlbrando on 2009-11-14
Ok, I installed RealFlight4.X in Karmic and it seems to run well.  I Started the wine configuration utility and set permissions for all the drives.  Except my USB ports apparently.  At least I think this is the problem.

It is telling me that my Interlink Controller is not plugged in no matter which port it is on.  How do I enable the usb ports in wine?

---

### Post by dlbrando on 2009-11-14
I am pretty sure that I just need to link the usb libraries to wine using something like ln -s, but I am not sure which libraries or how

---

### Post by dlbrando on 2009-11-14
[http://wiki.winehq.org/USB?highlight=%28usb%29](http://wiki.winehq.org/USB?highlight=%28usb%29)

so I think this is getting to where I need to be, but I am not sure exactly what to do with the two files at the top.

---

### Post by dlbrando on 2009-11-14
So after trying to get everything to work, I get this output:

> megavid@megavid-laptop:~$ cd ~/wine-git
megavid@megavid-laptop:~/wine-git$ git config remote.origin.url
git://source.winehq.org/git/wine.git
megavid@megavid-laptop:~/wine-git$ git am *.txt
previous rebase directory /home/megavid/wine-git/.git/rebase-apply still exists but mbox given.


where do I go from here?

---

