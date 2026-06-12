---
title: "Problem with command include in kile"
date: 2010-12-03
forum: General Help
---

### Post by housseinireza on 2010-12-03
Hello everybody

I'm using kile as latex editor. Ubuntu and Kile are up to date.

Now in my preamble I write the following code:

```
\include{layout}

\begin{document}

\include{titlepage}

\frontmatter

\tableofcontents

\mainmatter

\include{theory}
\include{measure}

\backmatter

\renewcommand{\refname}{Literaturverzeichnis}
\include{references}
\bibliography{bibtex/references-project1}{}
\bibliographystyle{abbrvdin}

\listoffigures

\include{symbols}

\end{document}
```

and I get problems compiling it:

```
Package inputenc Error:
```

But only if I add some text and character ä, ö and ü to the file measure.tex like:

```
\chapter{sfasfasf}
asfasd
asdasd
```

Why do I get an encoding problem in the second file but not in the first?

I'm usig the following encoding:

```
\usepackage[utf8]{inputenc}
```

Thanks for your help, I didn't found any solutions on the web or elsewhere.

---

