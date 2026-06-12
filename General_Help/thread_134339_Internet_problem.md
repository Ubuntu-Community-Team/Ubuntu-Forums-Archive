---
title: "Internet problem"
date: 2006-02-21
forum: General Help
---

### Post by bsmaat on 2006-02-21
I'm trying to install the eci-adsl drivers for my modem (bt voyager usb). However, when I try to install the .deb file provided i get this error message:

nut@ubuntu:~$ sudo dpkg -i /media/download/eciadsl-usermode_0.10-1_i386.deb
(Reading database ... 58812 files and directories currently installed.)
Preparing to replace eciadsl-usermode 0.10-1 (using .../eciadsl-usermode_0.10-1_i386.deb) ...
Unpacking replacement eciadsl-usermode ...
dpkg: dependency problems prevent configuration of eciadsl-usermode:
eciadsl-usermode depends on pppoe; however:
Package pppoe is not installed.
dpkg: error processing eciadsl-usermode (--install):
dependency problems - leaving unconfigured
Errors were encountered while processing:
eciadsl-usermode

I'm kind of new to linux, so help is greatly appreciated. What exactly is pppoe. The drivers are from [http://eciadsl.flashtux.org/](http://eciadsl.flashtux.org/)

Thanks in advance, you're life savers :)

Edit: I forgot to google pppoe (I DID GOOGLE!) so I'll have a search now whilst you lot a helpin me :p

I figure I need to install build-essential, but how would I get hold of that if I can't access the internet yet on my ubuntu box. I can download here but where would I download from and how would I download it? Thanks

---

### Post by bsmaat on 2006-02-21
bump

---

### Post by free0n on 2006-02-21
The package is looking for pppoe which from the error doesn't look like it's installed. 

Try going to 
 -> System
 -> Administration
 -> Synaptic
 -> Search for pppoe
 -> Click the checkbox and install it.

After that try running the deb package again.

---

