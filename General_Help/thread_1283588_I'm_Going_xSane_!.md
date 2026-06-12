---
title: "I'm Going xSane !"
date: 2009-10-05
forum: General Help
---

### Post by CaptainJackSpratt on 2009-10-05
I've scanned and searched posts and tried the lot but still XSANE gives me an error in the arguments !
 
scanimage -L returns me a lovely string telling me that my scanner is an Agfa Snapscan e52 (which it is) and connected to the usb. But I still get an argument error when using XSANE !
 
Help - I have the original scanner disk with .bin's and still that doesn't help.
 
Is there other software that I can use - I need to use my scannner !
 
Thanks

---

### Post by CaptainJackSpratt on 2009-10-06
more info...
 
On a fresh (and working) Ubuntu desktop install I plug in the scannner and then fire up the pre-installed Xsane application.  I get this error message.
 
I hope someone can point me in the right direction.

---

### Post by StuartN on 2009-10-06
> **CaptainJackSpratt said:**
> more info...
 
On a fresh (and working) Ubuntu desktop install I plug in the scannner and then fire up the pre-installed Xsane application.  I get this error message.
 
I hope someone can point me in the right direction.

*"the Snape25.bin file needed to be copied in the /usr/share/sane/snapscan/ directory and there we go :-) (that file can be extracted with cabextract from the official Agfa download, that was intended for Windows)"*

- [http://vandenabeele.com/Agfa-snapscan-e25-on-Ubuntu](http://vandenabeele.com/Agfa-snapscan-e25-on-Ubuntu)

*"/etc/sane.d/snapscan.conf required modification to point to the snape52.bin firmware."*

- [https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/110111](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/110111)

---

### Post by CaptainJackSpratt on 2009-10-06
Many thanks Stuart, unfortunately I have tried this already and still no joy.

---

