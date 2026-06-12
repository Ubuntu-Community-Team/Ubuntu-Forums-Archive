---
title: "inkscape 0.46 on 9.10"
date: 2009-12-18
forum: General Help
---

### Post by tenaru on 2009-12-18
Hi, 

My question is related to "how/when one can install an earlier version of a program on ubuntu?" In particular  I would like to use inkscape 0.46 (latest version 0.47) on ubuntu 9.10.

I have tried synaptic package manager -> package -> force version, but it is gray (not choosable). 

I have tried "sudo aptitude install inkscape=0.46", but it responds by saying there is no such version, and installs version 0.47. 

Is there another way to do it? 

Thank you.

Note: I want version inkscape 0.46, because in 0.47 a feauture (text appearing properly as text in eps) is broken.

---

### Post by Ylon on 2009-12-18
Try: 

**sudo apt-get autoremove inkscape**
then: [install this package](http://mirrors.cat.pdx.edu/ubuntu/pool/main/i/inkscape/inkscape_0.46-5ubuntu4_i386.deb)
([other option](http://mirrors.cat.pdx.edu/ubuntu/pool/main/i/inkscape/?order=d) )

The way it work (for future needs):
[input search](http://www.google.com/search?&q=inkscape+ubuntu+deb+%22index+of%22), remove, install.

---

### Post by tenaru on 2009-12-24
Thank you. Your solution works perfectly.

---

