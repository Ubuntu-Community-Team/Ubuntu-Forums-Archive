---
title: "texlive + revtex + pdflatex = rasterized fonts"
date: 2012-02-21
forum: General Help
---

### Post by Dimone on 2012-02-21
Hi,

I try to compose a scientific paper using standard texlive and with revtex. And I want to have PDF as output. So, I use texworks with pdflatex.

And here I've got very strange behaviour. When I use this toolchain to create PDF, I get raster fonts.

It is strange not only because it happens, but because 
[LIST]
[*] when I create PDF using general latex + dvipdf, the fonts are vector;
[*] if I do not use revtex, and use pdflatex, the fonts are vector;
[*] after I've changed all .map files in /etc/updmap.d from MixedMap to Map, the hello-world revtex document is compiled with vector fonts (but the whole article still got raster fonts... by the way, math formulas in the article have vector fonts);
[*] the same tex source is compiled under windows with latest texlive and revtex and pdflatex and have vector fonts (note, however, that, in ubuntu it seems, that it is not latest texlive and revtex versions).
[/LIST]

Here [https://wiki.archlinux.org/index.php/TeX_Live_FAQ]("https://wiki.archlinux.org/index.php/TeX_Live_FAQ") (Q: pdftex and/or dvips uses bitmap fonts instead of type1 postscript fonts...) some general information about this problem in texlive is given, however, as I understand if dvipdf works OK, then pdflatex should work either. But in my case dvipdf works and pdflatex do not. And during compilation pdflatex do not report any errors like "font is not found". And after updmap command metafont is used to generate fonts (which, as I understand should result in vector fonts).

Note, that I'm just latex user, not guru, so I do not understand well all this infrastructure and kinds of fonts etc. I can't even be aware, that I understand, which fonts are used during pdf generation. And I definitely do not understand, how do I know if those fonts are raster or vector (if somebody can point me to this information, thanks).

If somebody can give some ideas about how can I debug this or how this issue can be solved, or to point me to some resources, where I can get more info, I would really appreceate this.



Thanks in advace.

---

### Post by blegat on 2012-05-01
Maybe you are using
\usepackage[T1]{fontenc}

Try to remove that line

---

### Post by Dimone on 2012-05-02
Little bit too late, as I've switched to windows machine totally (at least for now) so, I cannot even check if it works. Anyway, thanks. Hope, york reply will help to somebody else.

Just to note: I think, there indeed was that line with fontenc.

---

