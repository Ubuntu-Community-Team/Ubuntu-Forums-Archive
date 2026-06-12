---
title: "XeTeX segfaults with custom fonts"
date: 2011-03-07
forum: General Help
---

### Post by Dingbats on 2011-03-07
Yesterday, I installed the Adobe Font Forge fonts.  They're all OpenType fonts and reside in ~/.fonts.  Since around the time when I was fiddling with them, XeTeX started segfaulting whenever I used one of them.  Any other font works fine.

The strange thing is that I had one font already in ~/.fonts before I installed all of the new ones, which did work fine, but which now causes a segfault.

The LaTeX file looks like this:

```
\documentclass[a4paper,12pt]{article}

\usepackage{xltxtra}

\setmainfont[Mapping=tex-text]{Sabon LT Std}

\title{Test}
\author{}
\date{}

\begin{document}
\maketitle

\section{Testing testing}
Test!

\end{document}
```

When I run *xelatex test.tex*, it segfaults and produces the log file I've attached to this post (renamed to test.txt from test.log).

*But*, when I run xelatex with the *-no-pdf* switch, it produces a file test.xdv without complaining.  When I then run *xdvipdfmx -vv test.xdv*, it segfaults and outputs to stdout what I've attached as a file error.txt.

I suspect it might have something to do with system font settings that may have been changed by Fontmatrix while I was browsing my fonts, perhaps doing something that I didn't understand and messed things up.  But I don't know which settings/config files/etc that may have been affected.

Any pointers in any direction would be greatly appreciated!

---

### Post by Dingbats on 2011-03-08
Bump...

If anyone could just point me towards what fonts settings and directories exist and may be involved in this, I could research it further.

---

### Post by Dingbats on 2011-03-11
One last attempt...

Converting the fonts to truetype and moving them to /usr/share/fonts/truetype didn't work.

---

### Post by Dingbats on 2011-03-13
I solved it!  Running fc-cache -f fixed it.

---

### Post by llamabr on 2011-03-13
Well done.  It's fun when you can report that something you did for yourself was successful.

---

