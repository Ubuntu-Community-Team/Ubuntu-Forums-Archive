---
title: "Graphic editing capabilities broken with texlive-2009 upgrade"
date: 2010-05-09
forum: General Help
---

### Post by mehmet.ali.anil on 2010-05-09
When I upgraded from Karmic to Lucid, I guess one of those upgrades was the tex engine, it was upgraded to texlive 2009.

Though It can render everything I could render beforehand, I am having trouble about one thing. I cannot use the additional preferences that can be used to edit an image when using \includegraphics function.

For example:

\begin{figure} [H]
\centering
\includegraphics[**width=0.7\linewidth,angle=-90,trim = 5mm 8mm 10mm 0mm, clip**]{example.ps}
\end{figure}

Used to rotate my ps file, trim it, then scale it as specified. 
Now, I get an error:

./Rapor.tex:59:Illegal unit of measure (pt inserted) ...e=-90,trim = 5mm 8mm 10mm 0mm, clip]{example.ps}

If there is only [**width=\linewidth**] tex doesn't recognize \linewidth and prints:


./Rapor.tex:59:Missing number, treated as zero...\includegraphics[width=\linewidth]{example.ps}

and the output file has the text within the square brackets, rather than the image. 

Somehow there is a problem or a change in how this usage is interpreted. I am using:

\usepackage{float}
\usepackage{graphicx}

packages that are related to graphics.

I'm using Kile 2.0.85, but the problem is editor independent, I get the same results with Texmaker.
I am using the exact same .tex sources that I used with Karmic.

What I've tried:
I installed texlive packages from scratch, with Kile.
I changed the graphicx.sty file with a version that I found on the net.

Those didn't help.

Is it a common problem?
I need help about this.

Thanks in advance.
M.Ali

---

### Post by mehmet.ali.anil on 2010-05-10
I'm copying this from Latex Comminity Forum:

I guess I found out what was the problem, but it is still an issue for me:

An easy example would be:
```

\listfiles
\documentclass[a4paper,10pt]{article}
\usepackage[turkish]{babel}
\usepackage{graphicx}
\usepackage{float}
\usepackage{xkeyval}

\begin{document}
	\begin{figure}
	\centering
	\includegraphics[width=0.5\linewidth]{devre1.ps}
	\end{figure}
\end{document}

```

Which outputs:
```
*****
*****     LaTeX output: 
*****     cd "/home/mali/Documents/Analog Elektronik Laboratuar&#305;/6"
*****     latex -interaction=nonstopmode 'Rapor2.tex'
*****
This is pdfTeX, Version 3.1415926-1.40.10 (TeX Live 2009/Debian)
 restricted \write18 enabled.
entering extended mode
(./Rapor2.tex
LaTeX2e &lt;2009/09/24&gt;
Babel &lt;v3.8l&gt; and hyphenation patterns for english, usenglishmax, dumylang, noh
yphenation, farsi, arabic, croatian, bulgarian, ukrainian, russian, czech, slov
ak, danish, dutch, finnish, french, basque, ngerman, german, german-x-2009-06-1
9, ngerman-x-2009-06-19, ibycus, monogreek, greek, ancientgreek, hungarian, san
skrit, italian, latin, latvian, lithuanian, mongolian2a, mongolian, bokmal, nyn
orsk, romanian, irish, coptic, serbian, turkish, welsh, esperanto, uppersorbian
, estonian, indonesian, interlingua, icelandic, kurmanji, slovenian, polish, po
rtuguese, spanish, galician, catalan, swedish, ukenglish, pinyin, loaded.
(/usr/share/texmf-texlive/tex/latex/base/article.cls
Document Class: article 2007/10/19 v1.4h Standard LaTeX document class
(/usr/share/texmf-texlive/tex/latex/base/size10.clo))
(/usr/share/texmf-texlive/tex/latex/graphics/graphicx.sty
(/usr/share/texmf-texlive/tex/latex/graphics/keyval.sty)
(/usr/share/texmf-texlive/tex/latex/graphics/graphics.sty
(/usr/share/texmf-texlive/tex/latex/graphics/trig.sty)
(/etc/texmf/tex/latex/config/graphics.cfg)
(/usr/share/texmf-texlive/tex/latex/graphics/dvips.def)))
(/usr/share/texmf-texlive/tex/latex/xkeyval/xkeyval.sty
(/usr/share/texmf-texlive/tex/generic/xkeyval/xkeyval.tex))
(/var/lib/texmf/tex/generic/babel/babel.sty
(/usr/share/texmf-texlive/tex/generic/babel/turkish.ldf
(/usr/share/texmf-texlive/tex/generic/babel/babel.def))) (./Rapor2.aux)
! Missing number, treated as zero.
&lt;to be read again&gt; 
                   \endgroup 
l.11 ...degraphics[width=0.5\linewidth]{devre1.ps}
                                                  
! Illegal unit of measure (pt inserted).
&lt;to be read again&gt; 
                   \endgroup 
l.11 ...degraphics[width=0.5\linewidth]{devre1.ps}
                                                  
[1] (./Rapor2.aux)

 *File List*
 article.cls    2007/10/19 v1.4h Standard LaTeX document class
  size10.clo    2007/10/19 v1.4h Standard LaTeX file (size option)
graphicx.sty    1999/02/16 v1.0f Enhanced LaTeX Graphics (DPC,SPQR)
  keyval.sty    1999/03/16 v1.13 key=value parser (DPC)
graphics.sty    2009/02/05 v1.0o Standard LaTeX Graphics (DPC,SPQR)
    trig.sty    1999/03/16 v1.09 sin cos tan (DPC)
graphics.cfg    2009/08/28 v1.8 graphics configuration of TeX Live
   dvips.def    1999/02/16 v3.0i Driver-dependant file (DPC,SPQR)
 xkeyval.sty    2008/08/13 v2.6a package option processing (HA)
 xkeyval.tex    2008/08/13 v2.6a key=value parser (HA)
   babel.sty    2008/07/06 v3.8l The Babel package
 turkish.ldf    2005/03/31 v1.2m Turkish support from the babel system
 ***********

 )
(see the transcript file for additional information)
Output written on Rapor2.dvi (1 page, 224 bytes).
Transcript written on Rapor2.log.
```

And the result is 1.pdf attached to this thread.

But when I remove the package babel for turkish, the code is compiled:

```

\listfiles
\documentclass[a4paper,10pt]{article}
\usepackage{graphicx}
\usepackage{float}
\usepackage{xkeyval}

\begin{document}
	\begin{figure}
	\centering
	\includegraphics[width=0.5\linewidth]{devre1.ps}
	\end{figure}
\end{document}

```

```

*****
*****     LaTeX output: 
*****     cd "/home/mali/Documents/Analog Elektronik Laboratuar&#305;/6"
*****     latex -interaction=nonstopmode 'Rapor2.tex'
*****
This is pdfTeX, Version 3.1415926-1.40.10 (TeX Live 2009/Debian)
 restricted \write18 enabled.
entering extended mode
(./Rapor2.tex
LaTeX2e &lt;2009/09/24&gt;
Babel &lt;v3.8l&gt; and hyphenation patterns for english, usenglishmax, dumylang, noh
yphenation, farsi, arabic, croatian, bulgarian, ukrainian, russian, czech, slov
ak, danish, dutch, finnish, french, basque, ngerman, german, german-x-2009-06-1
9, ngerman-x-2009-06-19, ibycus, monogreek, greek, ancientgreek, hungarian, san
skrit, italian, latin, latvian, lithuanian, mongolian2a, mongolian, bokmal, nyn
orsk, romanian, irish, coptic, serbian, turkish, welsh, esperanto, uppersorbian
, estonian, indonesian, interlingua, icelandic, kurmanji, slovenian, polish, po
rtuguese, spanish, galician, catalan, swedish, ukenglish, pinyin, loaded.
(/usr/share/texmf-texlive/tex/latex/base/article.cls
Document Class: article 2007/10/19 v1.4h Standard LaTeX document class
(/usr/share/texmf-texlive/tex/latex/base/size10.clo))
(/usr/share/texmf-texlive/tex/latex/graphics/graphicx.sty
(/usr/share/texmf-texlive/tex/latex/graphics/keyval.sty)
(/usr/share/texmf-texlive/tex/latex/graphics/graphics.sty
(/usr/share/texmf-texlive/tex/latex/graphics/trig.sty)
(/etc/texmf/tex/latex/config/graphics.cfg)
(/usr/share/texmf-texlive/tex/latex/graphics/dvips.def)))
(/usr/share/texmf-texlive/tex/latex/xkeyval/xkeyval.sty
(/usr/share/texmf-texlive/tex/generic/xkeyval/xkeyval.tex)) (./Rapor2.aux)
<devre1.ps> [1] (./Rapor2.aux) *File List* article.cls 2007/10/19 v1.4h Standard LaTeX document class size10.clo 2007/10/19 v1.4h Standard LaTeX file (size option) graphicx.sty 1999/02/16 v1.0f Enhanced LaTeX Graphics (DPC,SPQR) keyval.sty 1999/03/16 v1.13 key=value parser (DPC) graphics.sty 2009/02/05 v1.0o Standard LaTeX Graphics (DPC,SPQR) trig.sty 1999/03/16 v1.09 sin cos tan (DPC) graphics.cfg 2009/08/28 v1.8 graphics configuration of TeX Live dvips.def 1999/02/16 v3.0i Driver-dependant file (DPC,SPQR) xkeyval.sty 2008/08/13 v2.6a package option processing (HA) xkeyval.tex 2008/08/13 v2.6a key=value parser (HA) devre1.ps Graphic file (type eps) *********** ) Output written on Rapor2.dvi (1 page, 276 bytes). Transcript written on Rapor2.log.

```
And the result is 2.pdf, which is what I desire, but I cannot remove babel, since I neeed those Turkish characters.

I recognized that babel is run from /var/lib/texmf/tex/generic/babel/babel.sty , which differs in place, I guess those are the packages that are left from Tetex.

So, babel turkish is broken so that it interferes with compilation in texlive 2009, or I am still using a legacy version.

M.Ali

---

