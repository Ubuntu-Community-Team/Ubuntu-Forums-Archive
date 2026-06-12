---
title: "apt-get autoremove"
date: 2009-12-26
forum: General Help
---

### Post by switch10 on 2009-12-26
I've been trying to figure out lately if I should use aptitude or apt-get.  from what I can gather the main difference between the 2 is that aptitude automatically removes dependent packages.  Well I dont mind running sudo apt-get autoremove every once in a while, but here is what I got...

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  anyevent-perl dvdrip-doc ffmpeg fping gocr gtk2-ex-formfactory-perl
  libavdevice52 libavfilter0 libevent-execflow-perl libevent-perl
  libevent-rpc-perl libintl-perl libio-socket-ssl-perl libjpeg-progs
  libnet-libidn-perl libnet-ssleay-perl libnetpbm10 libreadline5
  libxine1-ffmpeg lsdvd netpbm ogmtools subtitleripper transcode-utils
  transfig xine-ui
0 upgraded, 0 newly installed, 26 to remove and 11 not upgraded.
After this operation, 25.1MB disk space will be freed.
```

It wants to uninstall ffmpeg.  I use devede to make video dvds and im pretty sure it uses ffmpeg.  whats the deal with this?  

Thanks 

Dave

---

### Post by Manyette on 2009-12-26
Well, it is possible that there is installed a newer version of ffmpeg, and it is trying to remove and earlier version.  You could check that in synaptic, but that would be my best guess.

---

### Post by Mahngiel on 2009-12-26
it's amazing the things you see auto-remove want to be rid of.

just the other day it wanted to auto-remove 'mbr' (master boot record).
i was afraid to reboot my computer until i researched that grub2 had replaced it and it wasn't needed.  

for the most part, i *think* it knows what it's doing.

---

### Post by Manyette on 2009-12-27
Well, I haven't caught it in an error as yet, and have learned to trust it.  But I guess "trust but verify" is the best policy. Fortunately, Synaptic Package manager makes it easy to do.

---

### Post by switch10 on 2009-12-27
Hahah ok.  Im going to trust it knows what it is doing....

---

