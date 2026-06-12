---
title: "where to put latex style file"
date: 2009-11-18
forum: General Help
---

### Post by MichaelBurns on 2009-11-18
I installed the tex-live package and then ran latex on one of my *.tex files.  I got the error:

! LaTeX Error: File `paralist.sty' not found.

So, should I just download this file (from ctan.org or something)?  If so, where should I put it?  Do I need to run an update on the fndb (like in MikTeX)?

---

### Post by diesch on 2009-11-18
It's in *texlive-latex-extra*.

To manuanlly install LaTeX styles put them in a subdirectory of *~/ texmf/tex/latex/* or */usr/local/share/texmf/tex/latex/* and call *texhash*

---

### Post by MichaelBurns on 2009-11-18
Thanks, diesch.  Out of curiosity, how did you know which package that style file was in?

---

### Post by Chronon on 2009-11-18
You can google for "texlive paralist.sty karmic" or search synaptic for "paralist"

---

### Post by diesch on 2009-11-19
```
sudo apt-file search paralist.sty
```
(apt-file is not installed by default). Or you can search on 
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by MichaelBurns on 2009-11-19
Thanks, diesch.  I searched synaptic for "paralist" and it spit out the extra package.  That's like magic or something!

BTW, to former MikTeX users:  no fndb update required.  (I guess that this happens automatically, or maybe the whole LaTeX structure and compilation is such that a fndb is unnecessary.)

---

