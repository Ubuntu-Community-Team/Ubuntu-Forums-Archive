---
title: "Formatting the Chapter Page in Latex"
date: 2010-12-18
forum: General Help
---

### Post by yaami on 2010-12-18
Hi all,

I need some help in LaTeX. I would like to change the space that is highlighted (oval shaped) in the attached figure. Please let me know if it is possible, if so how to do it. 

I tried changing the \headsep and \headheight but it does not change. yeah changing them changes the header separation and height in the rest of the pages. But the separation in between the chapter and the page number does not change. This is a sample that produced the attached doc. 

```
\documentclass{report}
\usepackage{setspace}
\raggedright
   \setlength{\topmargin}{0.0in}
%   \setlength{\topmargin}{0.0in}
   \setlength{\headheight}{0.25in}
   \setlength{\headsep}{0.25in}
%   \setlength{\topskip}{0.25in}   % first line, down from page number
   \setlength{\textheight}{8.5in}   
   \setlength{\footskip}{0.5in}
   \setlength{\oddsidemargin}{0.5in}  % adds to default 1.0in
   \setlength{\evensidemargin}{0.5in} % ditto
   \setlength{\parindent}{30pt}   % somewhere between 0.3" and 0.5"
   \setlength{\textwidth}{6in}
   \setlength{\leftmargini}{3.5em}
   \setlength{\leftmarginii}{2.2em}
   \setlength{\leftmarginiii}{2.2em}
   \setlength{\leftmarginiv}{2.2em}
   \setlength{\leftmarginv}{2.2em}
   \setlength{\leftmarginvi}{2.2em}
   \setlength{\leftmargin}{\leftmargini}
   \setlength{\labelsep}{.5em}
   \setlength{\labelwidth}{ 1.5em}
   \pagenumbering{arabic}
   \pagestyle{myheadings}
   \markboth{}{}
   \if@draftVersion
      \markboth{\th@draftVersionStash}{\th@draftVersionStash}
   \fi
   \onecolumn
   \raggedbottom
   \normalsize
   \normalfont
\doublespace

\title{Some Title}
\author{Yaami}
\begin{document}
\maketitle
\tableofcontents
\chapter{First Chapter}
\thispagestyle{headings}
LaTeX has a very distinct style that is somewhat different from what your professors expect and want their student's papers to look like. Some professors will not accept papers without ragged right text, 12 pt font, and 1 inch margins. I recommend asking your professor for their guidelines before you write your first paper. Once you have their guidelines, the options below will help you make your paper's format exactly what they want.

LaTeX uses its professional typesetting engine to perfectly justify your text, just like professionally published books and journals. However, many professors prefer unjustified text that is aligned with the left edge and the right edge ragged, commonly known as ragged right or left-aligned text. To give your paper a ragged right edge, use the raggedright environment.
\newpage
This is new page.

LaTeX uses its professional typesetting engine to perfectly justify your text, just like professionally published books and journals. However, many professors prefer unjustified text that is aligned with the left edge and the right edge ragged, commonly known as ragged right or left-aligned text. To give your paper a ragged right edge, use the raggedright environment.

\end{document}
```
Please let me know how to do it. 
Thanks.

---

### Post by yaami on 2010-12-18
Hi all,

I need some help in LaTeX. I would like to change the space that is highlighted (oval shaped) in the attached figure. Please let me know if it is possible, if so how to do it. 

I tried changing the \headsep and \headheight but it does not change. yeah changing them changes the header separation and height in the rest of the pages. But the separation in between the chapter and the page number does not change. This is a sample that produced the attached doc. 

```
\documentclass{report}
\usepackage{setspace}
\raggedright
   \setlength{\topmargin}{0.0in}
%   \setlength{\topmargin}{0.0in}
   \setlength{\headheight}{0.25in}
   \setlength{\headsep}{0.25in}
%   \setlength{\topskip}{0.25in}   % first line, down from page number
   \setlength{\textheight}{8.5in}   
   \setlength{\footskip}{0.5in}
   \setlength{\oddsidemargin}{0.5in}  % adds to default 1.0in
   \setlength{\evensidemargin}{0.5in} % ditto
   \setlength{\parindent}{30pt}   % somewhere between 0.3" and 0.5"
   \setlength{\textwidth}{6in}
   \setlength{\leftmargini}{3.5em}
   \setlength{\leftmarginii}{2.2em}
   \setlength{\leftmarginiii}{2.2em}
   \setlength{\leftmarginiv}{2.2em}
   \setlength{\leftmarginv}{2.2em}
   \setlength{\leftmarginvi}{2.2em}
   \setlength{\leftmargin}{\leftmargini}
   \setlength{\labelsep}{.5em}
   \setlength{\labelwidth}{ 1.5em}
   \pagenumbering{arabic}
   \pagestyle{myheadings}
   \markboth{}{}
   \if@draftVersion
      \markboth{\th@draftVersionStash}{\th@draftVersionStash}
   \fi
   \onecolumn
   \raggedbottom
   \normalsize
   \normalfont
\doublespace

\title{Some Title}
\author{Yaami}
\begin{document}
\maketitle
\tableofcontents
\chapter{First Chapter}
\thispagestyle{headings}
LaTeX has a very distinct style that is somewhat different from what your professors expect and want their student's papers to look like. Some professors will not accept papers without ragged right text, 12 pt font, and 1 inch margins. I recommend asking your professor for their guidelines before you write your first paper. Once you have their guidelines, the options below will help you make your paper's format exactly what they want.

LaTeX uses its professional typesetting engine to perfectly justify your text, just like professionally published books and journals. However, many professors prefer unjustified text that is aligned with the left edge and the right edge ragged, commonly known as ragged right or left-aligned text. To give your paper a ragged right edge, use the raggedright environment.
\newpage
This is new page.

LaTeX uses its professional typesetting engine to perfectly justify your text, just like professionally published books and journals. However, many professors prefer unjustified text that is aligned with the left edge and the right edge ragged, commonly known as ragged right or left-aligned text. To give your paper a ragged right edge, use the raggedright environment.

\end{document}
```
Please let me know how to do it. 
Thanks.

---

### Post by cariboo on 2010-12-18
Please don't create multiple threads on the same subject, I have merged your two threads.

---

