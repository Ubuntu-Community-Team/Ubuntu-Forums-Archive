---
title: "OpenOffice and Java"
date: 2006-03-23
forum: General Help
---

### Post by Blutack on 2006-03-23
I have a long word document with graphs from excel which I want to edit on my Breezy system.  I have the OpenOffice 2.0 that was included with the ISO.  Unfortunatly when I import it I do not see the graphs, just a grey box where they should be.  Before Kubuntu I ran Knoppix for a bit and its OO.o 2.0 beta was quite happy opening the graphs.  However the Knoppix version had a Sun Microsystems logo on the splash screen.  I understand that parts of OO are underpinned by Java and because of the kubuntu philosophy I assume a stripped none java version has been installed.
Firstly is the lack of graphs due to the none java version...?
And if so can I install the java bits, do I need a new multiverse install of OO, or do I need to compile a new copy from OO.
This is extremely important to me and I know is not a problem with Kubuntu per se but I'm sure one of you helpful guys will know...
Thanks!

---

### Post by MartinG on 2006-03-23
The version of OOo supplied is not crippled, but the java substitute supplied seems to be inadequate (to put it kindly).  Try installing Sun's Java, e.g. via Automatix (the Kubuntu version).

---

### Post by Blutack on 2006-03-23
Great!  However my box @ home doesn't have a net connection.  I can only get on broadband and work and stick stuff on a flashdisk.  Can I download java straight from sun or from the ubuntu packages site?
Thanks

---

### Post by MartinG on 2006-03-23
Yes, you can get it from one of the extra repositories that Automatix enables.  Go to:
[ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/pool/i386/non-free/java](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/pool/i386/non-free/java)
and download the j2re package.

On your home computer cd to wherever you've got the package and run:```
sudo dpkg -i sun-j2re1.5*.deb
sudo update-alternatives --set java /usr/lib/j2re1.5-sun/bin/java
```That should do the trick.

---

### Post by Blutack on 2006-03-23
Awesome! Will try it tonight...

---

### Post by Blutack on 2006-03-23
Ahh Christ!  The firewall blocks access to ftp.  Probably to stop us downloading stuff...

---

### Post by MartinG on 2006-03-23
Do you have http access? If so, try:
[http://packages.freecontrib.org/ubuntu/plf/pool/i386/non-free/java/](http://packages.freecontrib.org/ubuntu/plf/pool/i386/non-free/java/)
which is the same repository.

---

### Post by Blutack on 2006-03-24
Excellent, am downloading now.  Will let you know if it solves my OO woes.

---

### Post by Blutack on 2006-04-05
Excellent - sorted.  Many Thanks

---

