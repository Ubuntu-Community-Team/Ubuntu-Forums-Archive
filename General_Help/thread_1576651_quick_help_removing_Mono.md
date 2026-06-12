---
title: "quick help removing Mono"
date: 2010-09-17
forum: General Help
---

### Post by raafaell on 2010-09-17
I installed Mono 2.4 and I am struggling myself to remove all folders related to mono.. I didn't install from _Synaptic_ so it's not just 'apt-get autoremove mono', I used the tarball... do you know how to remove all files from the installation? 

Thanks in advance!

---

### Post by raafaell on 2010-09-17
anyone?

---

### Post by directhex on 2010-09-18
Which prefix did you install it to, i.e. did you specify "--prefix=/usr/lib" or similar?

Also, if you still have the folder you compiled it inside, then run "make uninstall"

---

### Post by raafaell on 2010-09-18
> **directhex said:**
> Which prefix did you install it to, i.e. did you specify "--prefix=/usr/lib" or similar?

Also, if you still have the folder you compiled it inside, then run "make uninstall"

Thanks, I was kinda confused how to remove it, and so I started searching for any files related to Mono, and removing manually, but that didn't work out, so I just reformatted my machine. 

Thanks for the info..

---

