---
title: "Cannot install anything in Ubuntu 9.10 RC"
date: 2009-10-24
forum: General Help
---

### Post by Sinani201 on 2009-10-24
I just got a clean installation of the new Ubuntu 9.10 RC, and I can't install anything. Everything in the Ubuntu Software Center says that it is "Not Available in the Current Data," if I go into Synaptic Package Manager, all of the checkboxes are green as if everything in the repositories is installed on my computer, and if I use apt-get install for a package it says that the package is not found. Additionally, when Rhythmbox searched the for mp3 codec, it couldn't find anything (normally it points to Gstreamer). I can browse the web in Firefox normally.

I am running the Ubuntu 9.10 RC in the latest version of Virtualbox on Mac OS X Snow Leopard 10.6.1 Macbook Pro 13" Unibody 2.26 GHz Intel Core 2 Duo with 2GB of RAM (Ubuntu uses 1000MB when in the virtualization environment).

Also, as a side note, has the Wine HQ made a version of Wine for 9.10? It doesn't have instructions for it on their website.

---

### Post by Sinani201 on 2009-10-24
Sorry for the double post, but since this got to the second page, I figured it needed a bump. Please help!

---

### Post by NCLI on 2009-10-24
Have you tried running "sudo apt-get update"?

---

### Post by howefield on 2009-10-24
Looks like this one

[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/428414](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/428414)

As suggested sudo apt-get update may fix it.

Wine don't make specific versions for Ubuntu, least not that I'm aware of, the current version of Wine is 1.1.32 and the version in the Karmic repository is 1.1.31. If you must have the latest Wine, install the WineHQ APT Repository

---

### Post by wilee-nilee on 2009-10-24
Have you gone into software sources and made sure the read from the CD is off and it is calling the repositories.

---

### Post by Sinani201 on 2009-10-24
Thanks! sudo apt-get update worked.

---

