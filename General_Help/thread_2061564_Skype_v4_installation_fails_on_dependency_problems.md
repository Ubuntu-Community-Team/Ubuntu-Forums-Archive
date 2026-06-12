---
title: "Skype v4 installation fails on dependency problems"
date: 2012-09-22
forum: General Help
---

### Post by pwabrahams on 2012-09-22
I'm trying to install the new Skype v4 for Linux on my Kubuntu 12.04 system.  The installation fails on dependency problems, which ultimately seem to reduce to just one:
```
libc6-i386:
  Depends: libc6 (=2.15-0ubuntu10) but 2.15-0ubuntu10.1 is to be installed
```
How can I get past this?

---

### Post by Thongar on 2012-09-23
I would install gdebi-qt from either synaptic or do a sudo apt-get install gdebi-qt.  

Then launch gdebi-qt from the menu and open your skype package from there to install it.

Reason being is that gdebi will auto resolve those dependencies for any other packages that you download outside of the software manager.  Hope this helps :).

---

### Post by pwabrahams on 2012-09-23
Perhaps I'm missing a repository, but apt-get can't find **gdebi-qt**.

---

