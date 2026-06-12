---
title: "Font shape `OMS/cmss/m/n' undefined for symbol `textbullet' in Latex Beamer"
date: 2011-03-06
forum: General Help
---

### Post by simon303 on 2011-03-06
Hi,

I am using Beamer to make a presentation in Latex.  I am basically just modifying the default theme and want circles for bullet points, so I added the line
```
\setbeamertemplate{itemize items}[circle]
```
But now, when I use
```
\begin{itemize}
\item first item
\item second item
\item more items...
\end{itemize}
```
I get errors along the lines of
```
LaTeX Font Warning: Font shape `OMS/cmss/m/n' undefined
(Font)              using `OMS/cmsy/m/n' instead
(Font)              for symbol `textbullet' on input line 48.
```

I have all the texlive reccomended and extra packages installed, but I'm still getting the error.  Does anyone now how to stop this happening (i.e. where can I get the appropriate font/font extension?)

Simon

---

