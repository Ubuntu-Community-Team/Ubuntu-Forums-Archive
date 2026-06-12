---
title: "LaTeX verbatim environment crashes pdflatex with beamer document class in Ubuntu 9.04"
date: 2009-07-22
forum: General Help
---

### Post by newagelink on 2009-07-22
I'm running: [LIST]
[*]Ubuntu 9.04 - the *Jaunty Jackalope*
[*]pdflatex (pdftex?) [I don't know how to find the version number.]
[*]gedit
[/LIST]
I am new to LaTeX and beamer; I have spent some time learning LyX, but LyX apparently does a *horrible* job with the beamer document class, so I switched to editing .tex files in gedit.

The verbatim environment crashes pdflatex, even including the fragile option. (Do I speak correctly?) Please tell me how to fix this problem! I have a presentation Friday (24 July 2009).

Compare code A with code B (B shows the only changes):
Code B (kills pdflatex): ```
  \subsection{FORTRAN77?}
   \begin{frame}**[COLOR="Blue"][fragile][/COLOR]**
    \frametitle{FORTRAN77 is a simple programming language.}
    \begin{columns}
     \column{.5\textwidth}  
      [COLOR="Blue"][B]\begin{verbatim}
       I want code shown here!
      \end{verbatim}[/B][/COLOR] \pause
     \column{.5\textwidth}
      Common commands include:
      \begin{example}
       \begin{itemize}
        \item DO .. CONTINUE
        \item READ, WRITE
        \item OPEN, REWIND, CLOSE
        \item IF .. THEN, IF
        \item SUBROUTINE
       \end{itemize}
      \end{example}
    \end{columns}
   \end{frame}
```
Code A (runs fine): ```
  \subsection{FORTRAN77?}
   \begin{frame}
    \frametitle{FORTRAN77 is a simple programming language.}
    \begin{columns}
     \column{.5\textwidth}  
       \pause
     \column{.5\textwidth}
      Common commands include:
      \begin{example}
       \begin{itemize}
        \item DO .. CONTINUE
        \item READ, WRITE
        \item OPEN, REWIND, CLOSE
        \item IF .. THEN, IF
        \item SUBROUTINE
       \end{itemize}
      \end{example}
    \end{columns}
   \end{frame}
```
(By the way, should I be running "pdftex main.tex" or "pdflatex main.tex" in the gnome-terminal?)

---

