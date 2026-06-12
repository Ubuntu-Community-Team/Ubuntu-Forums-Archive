---
title: "Getting lyx to recognise a manual install of texlive"
date: 2011-09-01
forum: General Help
---

### Post by oldmankit on 2011-09-01
Hello,

I needed the most up-to-date texlive I could find and so installed it manually.  (I'm working on a completely clean install of Natty, BTW.)

I would like to get lyx to work with the now-existing texlive installation.  If you install lyx normally it will install a whole new bunch of texlive packages, for me a waste of my precious modem bandwidth, disk space, and most importantly, I don't think it'll be using the existing, up-to-date texlive.

I installed lyx using 'sudo apt-get --no-install-recommends lyx' and it installed the barebones, no texlive.  However, when I load any lyx document, it says:
> The selected document class
article
requires external files that are not available.  The document lcass can still be used, but the document cannot be compiled until the following prerequisites are installed:
article.cls

What should I do to fix this?

Thank you in advance :P,
Kit

(PS: The texlive install is working fine from the command line.  It *does* know about the article class.'

---

### Post by oldmankit on 2011-09-03
Bumpy bump.

---

### Post by oldmankit on 2011-09-04
Bump

---

### Post by oldmankit on 2011-09-10
Can anyone help?  I've done some searching and can't find an answer...

---

### Post by oldmankit on 2011-09-15
I'm still unable to use lyx. Please help!

---

### Post by nardis_Miles1 on 2012-01-25
I'm having similar problems. Lots of document classes are missing.

---

### Post by rplantz on 2012-02-19
I'm in the same situation. Two questions:

1. Is is possible to have both versions of texlive (2011 and Ubuntu's 2009) installed simultaneously?

2. Has anybody installed lyx by hand, instead of from the Ubuntu repositories, so it will use the manual install of texlive 2011?

---

