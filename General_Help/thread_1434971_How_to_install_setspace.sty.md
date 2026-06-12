---
title: "How to install setspace.sty"
date: 2010-03-20
forum: General Help
---

### Post by skytreader on 2010-03-20
Hi all. I've been LaTeXing when I found out that I do not have setspace.sty (i.e., LaTeX complains on the \usepackage{setspace} line. I tried to google for setspace.sty and found this:

[http://www.tex.ac.uk/tex-archive/macros/latex/contrib/setspace/setspace.sty](http://www.tex.ac.uk/tex-archive/macros/latex/contrib/setspace/setspace.sty)

Problem is, at usr/share/texmf-texlive/, I cannot add new files, let alone a new folder. Copy-paste doesn't work too. So, how can I get my setspace.sty?

Thanks!

---

### Post by Ubu-freak on 2010-03-26
You must have root privileges. Using terminal:

```

$ sudo cp /path/to/sty/file /usr/share/texmf-texlive/latex

```You should also checkout [http://www.tex.ac.uk/cgi-bin/texfaq2html?label=install-where](http://www.tex.ac.uk/cgi-bin/texfaq2html?label=install-where)

Alternatively, you could try

```

$ sudo apt-get install texlive-latex-extra

```

---

