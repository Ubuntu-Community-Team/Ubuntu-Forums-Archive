---
title: "tracker won't index pdf files"
date: 2011-09-03
forum: General Help
---

### Post by Sin@Sin-Sacrifice on 2011-09-03
Installed tracker from the ppa out of Ubuntu-tweak. Haven't used it for a while but need it again but now it's not indexing any pdf files. I've tried searches I know are in certain pdfs and none of them come up. The plain text docs in the same directory (or a sub-directory thereof) all show. Anything I'm missing?

---

### Post by Sin@Sin-Sacrifice on 2011-09-18
I fixed this by compiling tracker myself, turning on the pdf flag in ./configure  -- if anyone else is having this problem then just download the source, run ```
sudo build-dep tracker
```, then cd into the source dir after you unpack it and type ```
./configure --help
``` it explains how to enable the pdf bit as well as many others.

---

