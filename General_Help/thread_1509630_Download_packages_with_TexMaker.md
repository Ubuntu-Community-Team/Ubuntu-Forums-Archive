---
title: "Download packages with TexMaker"
date: 2010-06-14
forum: General Help
---

### Post by JCM_Pico on 2010-06-14
[SIZE=2]Hi there,
I've recently installed texmaker, and when I try to compile the documents that I built some time ago (after formanting my pc) this error mesage appear...
[/SIZE]
 p, li { white-space: pre-wrap; }  LOG FILE :
 This is pdfTeX, Version 3.1415926-1.40.10 (TeX Live 2009/Debian) (format=latex 2010.6.12) 14 JUN 2010 19:00
 entering extended mode
 restricted \write18 enabled.
 %&-line parsing enabled.
 **relatorio3.tex
 (./relatorio3.tex
 LaTeX2e <2009/09/24>
 Babel <v3.8l> and hyphenation patterns for english, usenglishmax, dumylang, noh
 yphenation, loaded.
 (/usr/share/texmf-texlive/tex/latex/base/report.cls
 Document Class: report 2007/10/19 v1.4h Standard LaTeX document class
 (/usr/share/texmf-texlive/tex/latex/base/size11.clo
 File: size11.clo 2007/10/19 v1.4h Standard LaTeX file (size option)
 )
 \c@part=\count79
 \c@chapter=\count80
 \c@section=\count81
 \c@subsection=\count82
 \c@subsubsection=\count83
 \c@paragraph=\count84
 \c@subparagraph=\count85
 \c@figure=\count86
 \c@table=\count87
 \abovecaptionskip=\skip41
 \belowcaptionskip=\skip42
 \bibindent=\dimen102
 )
 (/usr/share/texmf-texlive/tex/latex/graphics/graphicx.sty
 Package: graphicx 1999/02/16 v1.0f Enhanced LaTeX Graphics (DPC,SPQR)
 (/usr/share/texmf-texlive/tex/latex/graphics/keyval.sty
 Package: keyval 1999/03/16 v1.13 key=value parser (DPC)
 \KV@toks@=\toks14
 )
 (/usr/share/texmf-texlive/tex/latex/graphics/graphics.sty
 Package: graphics 2009/02/05 v1.0o Standard LaTeX Graphics (DPC,SPQR)
 (/usr/share/texmf-texlive/tex/latex/graphics/trig.sty
 Package: trig 1999/03/16 v1.09 sin cos tan (DPC)
 )
 (/etc/texmf/tex/latex/config/graphics.cfg
 File: graphics.cfg 2009/08/28 v1.8 graphics configuration of TeX Live
 )
 Package graphics Info: Driver file: dvips.def on input line 91.
 (/usr/share/texmf-texlive/tex/latex/graphics/dvips.def
 File: dvips.def 1999/02/16 v3.0i Driver-dependant file (DPC,SPQR)
 ))
 \Gin@req@height=\dimen103
 \Gin@req@width=\dimen104
 )
 (/usr/share/texmf-texlive/tex/generic/babel/babel.sty
 Package: babel 2008/07/06 v3.8l The Babel package
 (/usr/share/texmf-texlive/tex/generic/babel/portuges.ldf
 Language: portuges 2008/03/18 v1.2q Portuguese support from the babel system
 (/usr/share/texmf-texlive/tex/generic/babel/babel.def
 File: babel.def 2008/07/06 v3.8l Babel common definitions
 \babel@savecnt=\count88
 \U@D=\dimen105
 )
 Package babel Warning: No hyphenation patterns were loaded for
 (babel) the language `Portuguese'
 (babel) I will use the patterns loaded for \language=0 instead.
 \l@portuges = a dialect from \language0
 Package babel Info: Making " an active character on input line 145.
 )) (/usr/share/texmf-texlive/tex/latex/base/fontenc.sty
 Package: fontenc 2005/09/27 v1.99g Standard LaTeX package
 (/usr/share/texmf-texlive/tex/latex/base/t1enc.def
 File: t1enc.def 2005/09/27 v1.99g Standard LaTeX file
 LaTeX Font Info: Redeclaring font encoding T1 on input line 43.
 ))
 (/usr/share/texmf-texlive/tex/latex/ltxmisc/a4wide.sty
 Package: a4wide 1994/08/30
 (/usr/share/texmf-texlive/tex/latex/ntgclass/a4.sty
 Package: a4 2004/04/15 v1.2g A4 based page layout
 ))
 (/usr/share/texmf-texlive/tex/latex/jknapltx/mathrsfs.sty
 Package: mathrsfs 1996/01/01 Math RSFS package v1.0 (jk)
 \symrsfs=\mathgroup4
 )
 (/usr/share/texmf-texlive/tex/latex/amsfonts/amsfonts.sty
 Package: amsfonts 2009/06/22 v3.00 Basic AMSFonts support
 \@emptytoks=\toks15
 \symAMSa=\mathgroup5
 \symAMSb=\mathgroup6
 LaTeX Font Info: Overwriting math alphabet `\mathfrak' in version `bold'
 (Font) U/euf/m/n --> U/euf/b/n on input line 96.
 )
 ! LaTeX Error: File `empheq.sty' not found.
 Type X to quit or <RETURN> to proceed,
 or enter new name. (Default extension: sty)
 Enter file name:
 ! Emergency stop.
 <read *>
 l.10 \usepackage
 {subfigure}^^M
 *** (cannot \read from terminal in nonstop modes)
 Here is how much of TeX's memory you used:
 1133 strings out of 495062
 12881 string characters out of 1182644
 61757 words of memory out of 3000000
 4349 multiletter control sequences out of 15000+50000
 4709 words of font info for 16 fonts, out of 3000000 for 9000
 28 hyphenation exceptions out of 8191
 25i,0n,24p,215b,37s stack positions out of 5000i,500n,10000p,200000b,50000s
 No pages of output.

[SIZE=2]Does any body nows why TexMaker don't download the package that isn't found?
I'm trying to avoid the use of Kile since I'm in a Gnome environment... 
[/SIZE]

---

### Post by Stefan_K on 2010-06-28
Hi,

install the corresponding Ubuntu package, it might be texlive-latex3 or texlive-latex-extra or texlive-math-extra.

Stefan

---

### Post by puigpuig on 2012-09-11
For the Babel hyphenation patterns in spanish you should install texlive-lang-spanish. 

It will be similar with other languages.

---

### Post by oldos2er on 2012-09-11
Old thread closed. Please don't bump old threads.

---

