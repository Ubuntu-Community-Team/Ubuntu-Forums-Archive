---
title: "qt is there but not?"
date: 2006-03-19
forum: General Help
---

### Post by AnnihilationDreamscapes on 2006-03-19
I'm a Linux newbie but I've been poking around for a while now. I'm trying to install qtella. i've installed Kubuntu, as well as run automatix to get most of the stuff I need. However, when I run ./configure after xzf tar qtella0.6.5.tar.gz, it says that I have no c++, c, etc. etc. So I went back to the Qtella homepage and it says to go to trolltech to get the qt-mt (sp?) business. Trolltech is a website that sells some expensive software for Linux, Windows, and Macs (yuck). Anyway, what the crap am I supposed to download? And then what? Do I really need to pay money to get the stuff needed to run qtella? Please help.

---

### Post by cilynx on 2006-03-19
You need the development packages.  When you install a library from a package, all you get is the runtime.  You need to explicitly install the development extensions for whatever qtella's configure tells you you don't have.

---

### Post by Jucato on 2006-03-19
Is the build-essentials package installed? AFAIK that is needed to compile from source code.

---

### Post by njf on 2006-03-20
If u want to compile Qt based apps, I think u need to install the libqt3-mt-dev package.

---

