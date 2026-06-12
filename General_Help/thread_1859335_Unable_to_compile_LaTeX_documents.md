---
title: "Unable to compile LaTeX documents"
date: 2011-10-13
forum: General Help
---

### Post by wombat365 on 2011-10-13
Hello,

I'm running Ubuntu 10.10 (Maverick) on a Macbook 6-2. Nearly everything else works fine, but for some reason I'm unable to compile Latex documents.

Right now it dumps this error message when I try to compile my document:

```
This is pdfTeX, Version 3.1415926-1.40.10 (TeX Live 2009/Debian)
entering extended mode
(./theory4.tex
LaTeX2e <2009/09/24>
Babel <v3.8l> and hyphenation patterns for english, usenglishmax, dumylang, noh
yphenation, farsi, arabic, croatian, bulgarian, ukrainian, russian, czech, slov
ak, danish, dutch, finnish, french, basque, ngerman, german, german-x-2009-06-1
9, ngerman-x-2009-06-19, ibycus, monogreek, greek, ancientgreek, hungarian, san
skrit, italian, latin, latvian, lithuanian, mongolian2a, mongolian, bokmal, nyn
orsk, romanian, irish, coptic, serbian, turkish, welsh, esperanto, uppersorbian
, estonian, indonesian, interlingua, icelandic, kurmanji, slovenian, polish, po
rtuguese, spanish, galician, catalan, swedish, ukenglish, pinyin, loaded.

! LaTeX Error: Missing \begin{document}.

See the LaTeX manual or LaTeX Companion for explanation.
Type  H <return>  for immediate help.
 ...

 ...                                              
                                                  
l.1 e
     package[left=1in, right=1in, top=1in, bottom=1in]{geometry}
? X
No pages of output.
Transcript written on document.log.
```My .tex file begins like this:
```
epackage[left=1in, right=1in, top=1in, bottom=1in]{geometry}
\usepackage{graphicx}

\pagestyle{head}

\headrule \header{\textbf{Document Title}}{}{\textbf{Page
\thepage\ of \numpages}}

\pointsinmargin \printanswers

\setlength\answerlinelength{2in} \setlength\answerskip{0.3in}

\begin{document}
```So it does have a \begin{document}. I installed texlive-full using apt-get and still it won't compile. When I use MacTex on my Mac OS X partition it compiles fine.
Any idea why it won't work?

---

### Post by wt8008 on 2011-10-13
Are you using LaTeX code copied and pasted from somewhere? It appears the first lines are missing or incomplete.

---

