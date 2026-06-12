---
title: "virtualbox 4.1 with ubuntu 11.10"
date: 2011-10-19
forum: General Help
---

### Post by quackeroni_pizza on 2011-10-19
I upgraded to Ubuntu 11.10 and alongwith Virtualbox 4.1.4 but Virtualbox is giving weird libQtCore errors->

VirtualBox: supR3HardenedMainGetTrustedMain: dlopen("/usr/lib/virtualbox/VirtualBox.so",) failed: /usr/lib/i386-linux-gnu/libQtGui.so.4: undefined symbol: XISelectEvents

I tried reinstalling libqt4core, and libqt4-core but to no avail (Hint from: [http://ubuntuforums.org/showthread.php?t=1096150](http://ubuntuforums.org/showthread.php?t=1096150)

---

### Post by BlinkinCat on 2011-10-19
Did you install Virtualbox from the VB site?

That other fix would be worthless - too old

---

### Post by quackeroni_pizza on 2011-10-19
Yes I did.. I added appropriate repo lines in /etc/apt/sources.list

---

### Post by BlinkinCat on 2011-10-19
I'm certainly not an expert but I found that it was simply a matter of downloading program and clicking on file in downloads to install.

---

### Post by BlinkinCat on 2011-10-19
I then downloaded correct extension pack to allow for full screen within guest

Within guest devices install extension pack.

---

### Post by quackeroni_pizza on 2011-10-19
Well the program installs fine.. 
In both cases: apt-get update and "double-clicking" a deb file, the same process happens behind the scenes... 

Trying to use "aptitude" now to see if there are any broken packages, etc...

The vbox kernel module gets recompiled without trouble...

The error occurs when running virtualbox.

---

### Post by BlinkinCat on 2011-10-19
Sorry if I wasn't much help - just saying how I did it - good luck - :)

---

### Post by rarity on 2011-10-25
Hi!

I got the same error.
Installing the ati-driver (Ubuntu - Driver menu) solved the problem in my case.
I hope this will help you, too.

Greetings from Vienna
rarity

---

