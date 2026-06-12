---
title: "LaTeX class directory"
date: 2009-08-07
forum: General Help
---

### Post by infernus_crusher on 2009-08-07
If I want to add a custom class to be used with LaTeX \usepackage syntax, where do I put the .cls file in? This is assuming I install LaTeX from aptitude and nothing has been altered yet.

---

### Post by rafita on 2009-08-07
create a directory ~/texmf/tex/latex/misc and put the .cls file there

then run 

sudo texhash

---

