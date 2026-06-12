---
title: "A unique error, never seen this before..."
date: 2006-05-30
forum: General Help
---

### Post by Simimi on 2006-05-30
Well I keep getting this error, and it is keeping me from doing any updates at all to my OS...any ideas anyone? I am lost for ideas...

[http://pastebin.com/746937](http://pastebin.com/746937)

Yours, mimi

---

### Post by frodon on 2006-05-30
How did you try to update, command lines or synaptic ?
It's always easier to solve problems (like overwriting a file) using synaptic when you try to update your ubuntu box.

Useful link : [https://wiki.ubuntu.com/DapperUpgrades](https://wiki.ubuntu.com/DapperUpgrades)

---

### Post by Simimi on 2006-05-30
I did it through the terminal via sudo apt-get dist-upgrade
 I am still pretty new to Linux, so I try to do as much via the command line as I can, I'll try with synaptic, though I am not totally sure how to use it.
Thanks muchly!
 Mimi

---

### Post by aysiu on 2006-05-30
```
Removing `diversion of /usr/share/ubuntu-artwork/home/index.html to /usr/share/ubuntu-artwork/home/index-ubuntu.html by kubuntu-docs'
dpkg-divert: rename involves overwriting `/usr/share/ubuntu-artwork/home/index.html' with
  different file `/usr/share/ubuntu-artwork/home/index-ubuntu.html', not alloweddpkg: error processing kubuntu-docs (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 kubuntu-docs
E: Sub-process /usr/bin/dpkg returned an error code (1)
``` Sounds like a bug to me, definitely.

---

### Post by Simimi on 2006-05-30
A bug? So... I should go about reporting this then? what are the default bug report channels for the Ubuntu Dev Team?
 Yours,
  Mimi

---

### Post by Simimi on 2006-05-30
[QUOTE=Simimi]A bug? So... I should go about reporting this then? what are the default bug report channels for the Ubuntu Dev Team?
 Yours,
  Mimi[/QUOTE]

Also...I can not report that as a bug on the bug report, It keeps returning an error

 Still no luck with getting anything to update though...

---

### Post by aysiu on 2006-05-30
I usually report bugs here:

[https://launchpad.net/malone](https://launchpad.net/malone)

---

### Post by Simimi on 2006-05-30
[QUOTE=aysiu]I usually report bugs here:

[https://launchpad.net/malone](https://launchpad.net/malone)[/QUOTE]

Fixed it, I had actually...
dpkg-divert: rename involves overwriting `/usr/share/ubuntu-artwork/home/index.html'

You have to delete the index.html file.
YAY US!
 Mimi

---

### Post by aysiu on 2006-05-30
[QUOTE=Simimi]Fixed it, I had actually...
dpkg-divert: rename involves overwriting `/usr/share/ubuntu-artwork/home/index.html'

You have to delete the index.html file.
YAY US!
 Mimi[/QUOTE] Even though you fixed it, I'd still say that is a bug. You should file a bug report on it.

---

