---
title: "Xetex conflicts"
date: 2011-02-26
forum: General Help
---

### Post by Dingbats on 2011-02-26
I've written an article in Latex and thought it would be nice to spice it up with a nicer looking font, and the easiest way to do that it with Xetex.  Here's the beginning of the file:

```
\documentclass[a4paper,11pt]{article}

\usepackage{xltxtra}
\usepackage[swedish]{babel}
\usepackage{subfigure}
\usepackage{tipa}
\usepackage{gb4e}
\usepackage{natbib}
\usepackage{nomencl}
\usepackage{sectsty}
```

Running xelatex returns:

```
! Undefined control sequence.
<argument> r@tr\IeC 
                    {\"a}
l.81 \newlabel{tr\IeC {\"a}}{{13}{7}}
```

Line 81 is:

```
\end{xlist}
```

If I rearrange the usepackage lines so it loads xltxtra anywhere after gb4e, I get this error:

```
! Missing \endcsname inserted.
<to be read again> 
                   \sp 
l.690 ...fter\let\csname\next\string\`-^\endcsname
                                                   \tipagravecircumaccent
```

Line 690 doesn't exist.

The file compiles just fine with pdflatex (without xltxtra and the line that changes the font).

What's up with this?  It looks like a package conflict, but I'm totally stumped when it comes to tracking the problem down further than that.  Does anyone know anything?

---

### Post by wt8008 on 2011-02-26
If possible, can you post a minimal example so other users can try to compile the file to see if they can recreate the issue.

---

### Post by Dingbats on 2011-02-27
> **wt8008 said:**
> If possible, can you post a minimal example so other users can try to compile the file to see if they can recreate the issue.
I tried deleting everything between \begin{document} and \end{document}, but it still won't compile.  I'm attaching the whole file, and those created by natbib (when it did compile, without Xetex).

---

### Post by wt8008 on 2011-02-27
Unfortunately, when I move the \usepackage{xltxtra} to the top, above bable, and change the font to \setmainfont{Liberation Serif}, I cannot recreate the issue, and it produces a PDF.

I only use latex and have not used xelatex before.

---

### Post by Dingbats on 2011-02-27
> **wt8008 said:**
> Unfortunately, when I move the \usepackage{xltxtra} to the top, above bable, and change the font to \setmainfont{Liberation Serif}, I cannot recreate the issue, and it produces a PDF.

I only use latex and have not used xelatex before.
:|

I tried changing the font, but it still won't compile.

---

### Post by wt8008 on 2011-02-27
I don't use xetex so I have no idea what is causing your issue, on top of it not showing up on my system. The only thing that comes to my mind is some missing packages.

Sorry.

---

