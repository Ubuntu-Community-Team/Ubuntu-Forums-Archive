---
title: "TexWorks cannot find file"
date: 2012-08-22
forum: General Help
---

### Post by DWMoreau on 2012-08-22
I new Ubuntu user and cannot get TexWorks to find a image file. I am sure that the path is set correctly, but maybe it is not. I have tried every path I could think of as well. 

The image has the location:
/home/david/Schedule.jpg

I went to Preferences in tex and changed the 'Paths for tex and related programs' to:
/home/david

The tex program uses the preamble I have used a million times in windows. The program is:
\documentclass[12ppt]{article}
\usepackage{epsfig}
\usepackage{amsmath}
\usepackage{amssymb}
\usepackage[margin=1in]{geometry}
\usepackage{graphicx}
\newcommand{\tab}{\hspace*{1.75em}}
\DeclareGraphicsExtensions{.pdf,.png,.jpg,.eps}
\begin {document}
\begin{figure}
	\includegraphics[scale = .75]{Schedule.jpg}
\end{figure}
\end{document}

The error is:

LaTeX Warning: File `Schedule.jpg' not found on input line 16.
! Package pdftex.def Error: File `Schedule.jpg' not found.
See the pdftex.def package documentation for explanation.
Type  H <return>  for immediate help.
 ...                                                                                            
l.16 	\includegraphics[scale = .75]{Schedule.jpg}

---

### Post by Irihapeti on 2012-08-22
In my experience, the image either needs to be in the same directory as the document file, or else the path needs to be specified.

E.g.```

\includegraphics[scale = .75]{images/Schedule.jpg}
```

or

```
\includegraphics[scale = .75]{/home/username/images/Schedule.jpg}
```

I also discovered the \graphicspath command ([http://en.wikibooks.org/wiki/LaTeX/Importing_Graphics#Graphics_storage](http://en.wikibooks.org/wiki/LaTeX/Importing_Graphics#Graphics_storage)) which looks like it might be useful if you store your graphics files in a central location, such as /home/username/images.

---

