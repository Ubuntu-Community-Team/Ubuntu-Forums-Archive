---
title: "TikZ polynomials bug"
date: 2012-01-12
forum: General Help
---

### Post by mihas on 2012-01-12
Hi!

I've found a bug in Ubuntu's tikz distribution. Quadratic polynomials are not plotted correctly. 
Code:
```

\documentclass[10pt]{article}
\usepackage{pgf,tikz}
\usetikzlibrary{arrows}
\pagestyle{empty}
\begin{document}
\definecolor{uququq}{rgb}{0.25,0.25,0.25}
\definecolor{wwwwww}{rgb}{0.4,0.4,0.4}
\begin{tikzpicture}[line cap=round,line join=round,>=triangle 45,x=1.0cm,y=1.0cm]
\draw[->,color=black] (-2.5,0) -- (4.23,0);
\foreach \x in {-2,-1,1,2,3,4}
\draw[shift={(\x,0)},color=black] (0pt,2pt) -- (0pt,-2pt) node[below] {\footnotesize $\x$};
\draw[->,color=black] (0,-2.1) -- (0,3.92);
\foreach \y in {-2,-1,1,2,3}
\draw[shift={(0,\y)},color=black] (2pt,0pt) -- (-2pt,0pt) node[left] {\footnotesize $\y$};
\draw[color=black] (0pt,-10pt) node[right] {\footnotesize $0$};
\clip(-2.5,-2.1) rectangle (4.23,3.92);
\draw(-2.31,-1.11) -- (-1.12,-1.11);
\draw(-2.33,-0.7) -- (-1.14,-0.7);
\draw [domain=-2.5:4.23] plot(\x,{(--1-0*\x)/1});
\draw [samples=50,rotate around={0:(1,1)},xshift=1cm,yshift=1cm,line width=1.6pt] plot (\x,\x^2/2/0.5);
\draw [samples=50,rotate around={-180:(1,1)},xshift=1cm,yshift=1cm,color=wwwwww] plot (\x,\x^2/2/0.5);
\draw [dash pattern=on 3pt off 3pt] (1,-2.1) -- (1,3.92);
\begin{scriptsize}
\fill [color=black] (-1.6,-1.11) circle (1.5pt);
\draw[color=black] (-1.52,-0.89) node {$b = 1$};
\fill [color=black] (-1.62,-0.7) circle (1.5pt);
\draw[color=black] (-1.55,-0.49) node {$a = 1$};
\draw[color=black] (-1.39,1.15) node {$y_m$};
\draw[color=black] (-0.37,2.69) node {$y_1$};
\draw[color=wwwwww] (-0.35,-0.56) node {$y_2$};
\fill [color=uququq] (2,0) circle (1.5pt);
\draw[color=uququq] (2.4,0.15) node {$B = (2, 0)$};
\fill [color=uququq] (0,0) circle (1.5pt);
\draw[color=uququq] (0.4,0.15) node {$A = (0, 0)$};
\fill [color=uququq] (1,1) circle (1.5pt);
\draw[color=uququq] (1.6,1.15) node {$Vertex = (1, 1)$};
\end{scriptsize}
\end{tikzpicture}
\end{document}

```

How it is plotted:
[http://i.imgur.com/7HTIk.png](http://i.imgur.com/7HTIk.png)

How should be plotted:
[http://i.imgur.com/3bkib.png](http://i.imgur.com/3bkib.png)

---

