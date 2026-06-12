---
title: "Org-Mode export images and Latex"
date: 2010-12-11
forum: General Help
---

### Post by Axolotl9250 on 2010-12-11
I'm wondering if a fellow org-mode user can help me out with this.
I made an .org file like the following:
```
#+TITLE:Dissertation Data Analysis
#+AUTHOR: Ben J. Ward
#+OPTIONS: num:nil ^:nil f:nil
#+BABEL: :session *R* :results silent
#+LATEX_CLASS: article
#+LATEX_HEADER: \renewcommand*\familydefault{\sfdefault}
#+begin_src R :exports results
evolution <- read.csv(file="~/Evolution Results.csv", header=T)
library("lattice")
#+end_src

* Visualization of Data
** Overall trend in Minimum inhibitory concentration values over time.
#+srcname:fig1
#+begin_src R :results output :exports results :file fig1.pdf
 xyplot(MIC.~Challenge, data=evolution)
#+end_src

#attr_latex: width=0.8\textwidth,placement=[p]
#+label: fig:one
#+caption: Fig1. Overall increace in MIC values as challenges continue.
#+results: fig1
[[file:fig1.pdf]]
```And it produced the .pdf file of the image (although it didn't even want to do that initially. But when I try to export to pdf, I get nothing beyond the title and author, and I get a .tex intermediate file like the following. 
```

% Created 2010-12-11 Sat 21:17
\documentclass{article}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage{fixltx2e}
\usepackage{graphicx}
\usepackage{longtable}
\usepackage{float}
\usepackage{wrapfig}
\usepackage{soul}
\usepackage{textcomp}
\usepackage{marvosym}
\usepackage{wasysym}
\usepackage{latexsym}
\usepackage{amssymb}
\usepackage{hyperref}
\tolerance=1000
\usepackage[scaled]{uarial}
\usepackage{babel}
\renewcommand*\familydefault{\sfdefault}
\providecommand{\alert}[1]{\textbf{#1}}

\title{Dissertation Data Analysis}
\author{Ben J. Ward}
\date{11 December 2010}

\begin{document}

\maketitle



\end{document}

```Which suggest to me babel isnt working, although it's package is loaded in the header and so is wrapfig. But I'm getting absolutely no error messages so I don't really know what to do, this is the first time this has happened to me.

---

