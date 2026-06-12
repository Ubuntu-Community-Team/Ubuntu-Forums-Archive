---
title: "Trouble with &quot;Kile&quot;."
date: 2010-01-18
forum: General Help
---

### Post by jshort on 2010-01-18
I'm trying to create a document in Kile, but I'm having trouble getting the title of my report to show up in the LATEX document when I run "Quickbuild" on my tex. I get the text I write in between the section "\begin{document}" and "\end{document}", but no title appears.

This is what I have written up in my text screen (whenever I want the LATEX document, I save my work, then go to section "Build, -Compile, -TEX", and then I press the "Quickbuild" button).


\documentclass[a4paper,12pt]{article}

\usepackage[latin1]{inputenc}
\usepackage[english]{babel}
\usepackage{fontenc}
\usepackage{graphicx}

\usepackage[dvips]{hyperref}

\author{James Short}
\title{Relationship between Rationals and Integers}
\date{2010-01-18}

\begin{document}


 Kile sucks.
\end{document}

---

### Post by robozoid on 2010-01-27
you have to type \maketitle inside the \begin{document} \end{document} pairing. this is a latex issue, not kile.

---

