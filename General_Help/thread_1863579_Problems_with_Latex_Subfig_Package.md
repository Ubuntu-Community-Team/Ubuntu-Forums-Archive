---
title: "Problems with Latex Subfig Package"
date: 2011-10-18
forum: General Help
---

### Post by kingdogbert on 2011-10-18
I'm trying to compile a Latex document using subfigures with the subfig package.

```

\usepackage{subfigure}
\begin{document}

...

\begin{figure}[t,c]
\begin{center}
        \subfigure[\footnotesize{}]{\label{fig:example-a}\epsfig{file=figs/dummy.eps,height=1in}}
        \subfigure[\footnotesize{}]{\label{fig:example-b}\epsfig{file=figs/dummy.eps,height=1in}}
        \subfigure[\footnotesize{}]{\label{fig:example-c}\epsfig{file=figs/dummy.eps,height=1in}}
\end{center}
\caption{NEED CAPTION}
\label{fig:example}
\end{figure}

```

This code generates an "Undefined Control Sequence" error for the \subfigure command. If I switch to using the older deprecated subfigure package, it works fine. The problem is with specifically trying to use the subfig package. I've got texlive-latex-extra installed, which is where the subfig package is supposed to reside. What am I missing here? Thanks.

---

### Post by kingdogbert on 2011-10-18
Well, I think I found the problem. The texlive-latex-extra package in the software manager seems to include subfigure, not subfig. That would explain it. But then how do I get the subfig package?

---

