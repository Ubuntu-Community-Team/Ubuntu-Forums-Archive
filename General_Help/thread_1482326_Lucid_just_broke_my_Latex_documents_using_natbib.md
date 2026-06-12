---
title: "Lucid just broke my Latex documents using natbib"
date: 2010-05-13
forum: General Help
---

### Post by bongotastic on 2010-05-13
Anyone has had this problem and know of a work-around. I really didn't plan in not being able to compile some documents today!

The error message is that there is an additional } in the bbl files, which are NOT manually created in the first place.

Thanks,

Christian

---

### Post by vivien` on 2010-05-13
Can you be more specific? Do you use latex or pdflatex? Do you use bibtex? If you use bibtex, remove the bbl file and regenerate it with bibtex. Actually, it is probably better to remove all intermediate files (.aux, .bbl, .blg, .dvi, .out).

---

### Post by bongotastic on 2010-05-13
To be more specific, I'm using PDFLatex, on a Ubuntu 10.04 as upgraded from 9.10 last week. The projects that compiled before upgrading to Lucid are no longer compiling. After doing a bit of investigation, the culprit is the inclusion of the natbib package. bibtex works fine, and there are no unmatched brackets in the bbl file that is generated. The bbl file is the file identified by Kile as the culprit. Deleting all intermediate files doesn't remove this behavior. The precise error message is the following:

Extra }, or forgotten \endgroup

This shows up for each citation in the bbl file. 


The only difference here is the upgrade from Karmic to Lucid. 

Thanks,

Christian

---

### Post by vivien` on 2010-05-13
No idea. Maybe you could provide a simplified example?

---

### Post by Lfulvipes on 2010-05-18
I am having the same problem. I have included a set of files that wont work on my home laptop (Ubuntu Lucid), but will at work (an old Bio-linux distribution). tester.bst is just a bibstyle file from systematic biology.

---

### Post by slightlyslow on 2010-05-27
Has anyone figured out how to solve this problem? I'm trying to use the style file for Systematic Biology (what Lfulvipes attached), and am having the same error messages that others have mentioned, e. g.

Extra }, or forgotten \endgroup

Any help would be greatly appreciated.

---

### Post by simonb66 on 2010-08-17
hi,

I'm running Debian, and I get the same error message. Has anyone been able to solve the problem? I will be most interested in the solution.

Thanks in advance,

Simon.

---

### Post by CUJimmy on 2011-03-01
Old thread, I know, but has anyone fixed this? I downloaded the latest version of natbib thinking it would solve the problem, but it hasn't! Any help appreciated...

Cheers, Jim

---

### Post by xarvia on 2011-04-12
Quick fix from [http://www.mrunix.de/forums/showthread.php?p=293721](http://www.mrunix.de/forums/showthread.php?p=293721) :
Put the following after \usepackage{natbib} and before \begin{document}

\renewcommand{\bibAnnoteFile}[1]{%
  \IfFileExists{#1}{\begin{quotation}\noindent\textsc{Key:} #1\\
  \textsc{Annotation:}\ \input{#1}\end{quotation}}{}}

\renewcommand{\bibAnnote}[2]{%
  \begin{quotation}\noindent\textsc{Key:} #1\\
  \textsc{Annotation:}\ #2\end{quotation}}


It appears this is a known compatibility issue between newer versions of natbib and bst files generated with older versions of makebst. (Alternatively you could modify your bst)

---

