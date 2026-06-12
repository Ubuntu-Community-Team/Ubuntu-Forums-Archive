---
title: "Nvidia GT430 Problem"
date: 2011-05-04
forum: General Help
---

### Post by Jerry N on 2011-05-04
I replaced my old Geforce 7600 card with a new Gt430 card on my secondary computer.  It works perfectly in Windows 7 with the downloaded drivers but I haven't been able to get any drivers in Ubuntu 10.04.  I followed the instructions at [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates) but when I tried to do a "sudo apt-get update" I got a 404 error message.  I also tried the download script from Nvidia and got nowhere there too.  

Video speeds were definitely improved in Windows 7 and I am hoping for the same improvement in Ubuntu 10.04.  I'm using a dual core Athlon 3800 on Gigabyte motherboard with 2gb of DDR2 (This computer is about 5 years old).  Any thoughts?

Jerry

---

### Post by Jerry N on 2011-05-04
Never mind - I got the drivers loaded.  Big improvement on GLXGEARS performance but still not worth a cr*p for playing high definition .mts movie files from a Canon HD camcorder.  The standard movie player in Windows 7 performs much better.  

VLC in Linux is even worse than mplayer and Kino doesn't work at all.  

Jerry

---

### Post by Yellow Pasque on 2011-05-05
vlc doesn't support vdpau, and you have to specify that as the video ouput to get mplayer to use it...

---

