---
title: "Libreoffice trashed OpenOffice &amp; can't fix dependency hell"
date: 2011-01-09
forum: General Help
---

### Post by herdwick on 2011-01-09
I saw the announcement of the Ubuntu LibreOffice PPA on a blog which said it could install alongside OpenOffice, added the PPA then set about installing and OpenOffice was removed, LibreOffice also failed to install due to a conflict with OpenOffice.

Now I have neither !

The libreoffice install error is below. I have tried 

sudo apt-get -f install

which also results in the same error :-

dpkg: error processing /var/cache/apt/archives/libreoffice-common_1%3a3.3.0~rc2-3lucid1_all.deb (--unpack):
 trying to overwrite '/etc/bash_completion.d/ooffice.sh', which is also in package openoffice.org-common 1:3.2.0-7ubuntu4.1
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-common_1%3a3.3.0~rc2-3lucid1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

How can I move forward from here please !

---

### Post by BigCityCat on 2011-01-09
remove libre office and then do the following. After your done re install libre office.

You haven't completely removed openoffice.org before installing libreoffice, and now you package is corrupted. In order to solve the issue, you have to manually purge the offending package, that is openoffice.org-common. Use the following command:
Code:

sudo dpkg --purge openoffice.org-common

dpkg might fail due to dependent packages. If so, remove dependent packages first. After that you can complete the libreoffice installation, and remove all openoffice.org leftovers using the command
Code:

sudo apt-get purge openoffice*

---

### Post by herdwick on 2011-01-09
Thanks. Synaptic Package Manager came to the rescue with its "broken" filter allowing me to get to the bottom of it and remove / fix the offending items.

The command line stuff seemed to get hung up on dependencies and I couldn't remove things because of dependencies - Catch 22 !

Reloading from the PPA now. More errors but now I know how to fix 'em.

---

### Post by mike555 on 2011-01-09
You should be sure you have the right ppa ,
[http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu)

---

### Post by beesyell on 2011-01-09
me too, i have read a new post about libreoffice on omgubuntu.co.uk, tried it out and yeah it trashed my OOo. :((

I have tried doing the stuff you suggested, then tried installing OOo from the ubuntu software center, but still shows the same error messages :(

---

### Post by JohnnyBDallas on 2011-01-16
I have the same problem, did you ever find a solution?

---

### Post by TGBaker on 2011-01-18
Everything that I've seen is that you must uninstall OpenOffice before installing LibreOffice. They are mostly the same files reworked a bit.

---

### Post by mike555 on 2011-01-18
just follow directions here ;
[http://www.webupd8.org/2011/01/install-libreoffice-in-ubuntu-from.html](http://www.webupd8.org/2011/01/install-libreoffice-in-ubuntu-from.html)

 only thing I had to install dictionary to get spell checking..

---

### Post by uRock on 2011-01-18
Here's another great place to look. [http://libreofficeforum.org/](http://libreofficeforum.org/)

---

