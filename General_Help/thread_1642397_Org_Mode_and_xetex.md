---
title: "Org Mode and xetex"
date: 2010-12-10
forum: General Help
---

### Post by Axolotl9250 on 2010-12-10
Hi All, I'm trying to get Org mode to process through xetex, so far I've done this with setting the org-latex-to-pdf-process to "xelatex -interaction nonstopmode %b" I need xetex to use Arial and other font's on my system for my work. So If I make the beginning of a document like so:

```
#+TITLE:My First Try with Org Mode
#+AUTHOR: Ben.
#+OPTIONS: num:nil ^:nil f:nil
#+LATEX_HEADER: \usepackage{amscd}
#+BABEL: :session *R* :results silent
#+LATEX_CLASS: article
#+begin_LaTeX:
 \usepackage{xunicode}
 \usepackage{fontspec}
 \defaultfontfeatures{Mapping=tex-text.Ligatures=Common}
 \setmainfont{Arial}
#+end_LaTeX:
```Hello World, rest of biology report to follow.

And I export it to pdf, it will export, but It will not be in Arial. What do I need to do in order to get this to work. I haven't altered anything else about emacs or or mode other than org-latex-to-pdf-process.

Thanks,
Ben.

---

