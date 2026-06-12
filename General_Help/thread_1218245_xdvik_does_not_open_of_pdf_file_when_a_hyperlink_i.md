---
title: "xdvik does not open of pdf file when a hyperlink is clicked"
date: 2009-07-20
forum: General Help
---

### Post by centguy on 2009-07-20
I don't have this problem with latex/xdvik on other Linux OS except Ubuntu 8.04. Linux ubuntu804-32-dell 2.6.24-23-generic

Basically, I cannot click on a link  in xdvik window created by 
\href{file://absolutepath/a-pdf.pdf}{A pdf file} in a LaTeX source file.

I guess it is a xdvi or latex problem.

Anybody has any idea ?

Clicking on 
a link created by
say, \href{http://www.latex-community.org/forum}{forum}
gives me a window with the content:

xterm: Can't execvp lynx: No such file or directory


So useful info:

xdvik version 22.84.10 (Xaw toolkit)
Libraries: kpathsea version 3.5.6, T1lib version 5.0.1

ckgan@ubuntu804-32-dell:/media/ext3-datadisk/summary/tex$ latex --version
pdfTeX using libpoppler 3.141592-1.40.3-2.2 (Web2C 7.5.6)
kpathsea version 3.5.6
Copyright 2007 Peter Breitenlohner (eTeX)/Han The Thanh (pdfTeX).
Kpathsea is copyright 2007 Karl Berry and Olaf Weber.
There is NO warranty.  Redistribution of this software is
covered by the terms of both the pdfTeX using libpoppler copyright and
the Lesser GNU General Public License.
For more information about these matters, see the file
named COPYING and the pdfTeX using libpoppler source.
Primary author of pdfTeX using libpoppler: Peter Breitenlohner (eTeX)/Han The Th
anh (pdfTeX).
Kpathsea written by Karl Berry, Olaf Weber, and others.

Compiled with libpng 1.2.15beta5; using libpng 1.2.15beta5
Compiled with zlib 1.2.3.3; using zlib 1.2.3.3
Compiled with libpoppler version 3.00


okay, I hope I have done my part.

---

### Post by centguy on 2009-08-02
anybody can offer any help ? Or should I bother with the xdvi/later people ?
I don't have this problem on Fedora or CentOS.

---

