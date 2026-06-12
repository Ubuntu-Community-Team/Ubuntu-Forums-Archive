---
title: "Portable programs"
date: 2011-09-22
forum: General Help
---

### Post by papaapa on 2011-09-22
Hello,

I need two portable programs

1- I need portable Chromium Browser
(NOTE: I DON'T NEED CHROMIUM PORTABLE ANYMORE)

2- I need portable Wine.

Thanks in advance...

---

### Post by dino99 on 2011-09-22
you might not worry about "portable", use the regular one as most of them are built on cross platform.

sudo add-apt-repository ppa:ubuntu-wine/ppa

---

### Post by papaapa on 2011-09-22
Sorry I did not understand what you mean.
I need to add the Wine on my USB drive. So, i will open it on any machine which has Ubuntu. If type this on command line : sudo add-apt-repository ppa:ubuntu-wine/ppa It will install wine on Ubuntu which is not portable.

---

### Post by varunendra on 2011-09-22
Hi,

What's wrong with a "Live Persistent" installation on a thumb drive? With 4GB+ drives, the whole Ubuntu installation has become "portable" these days. :)

But if you have some specific requirements which a live usb can't meet while a portable wine can (although I can't think of such any), this may be interesting for you: [http://ubuntuforums.org/showthread.php?t=1153477](http://ubuntuforums.org/showthread.php?t=1153477)

---

### Post by papaapa on 2011-09-22
> **varunendra said:**
> Hi,

What's wrong with a "Live Persistent" installation on a thumb drive? With 4GB+ drives, the whole Ubuntu installation has become "portable" these days. :)

But if you have some specific requirements which a live usb can't meet while a portable wine can (although I can't think of such any), this may be interesting for you: [http://ubuntuforums.org/showthread.php?t=1153477](http://ubuntuforums.org/showthread.php?t=1153477)

Thank you for alternate solutions and for your interest, but i could not understand what is wrong with "portable wine" which is (i know that) easy to make. (Such these all: [http://portablelinuxapps.org/](http://portablelinuxapps.org/) ). I really need a portable wine. I know all the other alternate solutions.

---

### Post by papaapa on 2011-09-23
If there is no an official portable Wine, can I make a portable of Wine from intallation file (deb) or source code of Wine?

---

### Post by i.r.id10t on 2011-09-23
> **papaapa said:**
> If there is no an official portable Wine, can I make a portable of Wine from intallation file (deb) or source code of Wine?

Yes.  When you built it, target /media/DRIVELABEL and then write a little shell script that will add appropriate $PATH, $LD_LIBRARY_PATH, etc. entries.  You'll also need to relocate your (typical) ~/.wine directory to your external media.


Better would probably be to make your own custom live cd with Wine on it, change the boot menu to always include persistence, and just use a flash drive for your home directory.  Plug drive in, boot your custom disk, and off you go.

---

