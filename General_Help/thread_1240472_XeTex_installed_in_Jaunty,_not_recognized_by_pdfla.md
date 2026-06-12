---
title: "XeTex installed in Jaunty, not recognized by pdflatex"
date: 2009-08-14
forum: General Help
---

### Post by sierra1bravo on 2009-08-14
Hi 
I am new to XeTex, though not to LaTex. I am running Jaunty on a Lenovo Laptop, and had done a full Tex Live installation using apt-get. However, I am unable to compile a XeTex file:

```
$ pdflatex a.tex
! 
 ********************************************
 * XeTeX is required to compile this document.
 * Sorry!
 ********************************************.
\RequireXeTeX ...********************************}
                                                  \endgroup \fi 
l.18 \RequireXeTeX
```

Here's the output of dpkg:

```
$ dpkg-query -L texlive-xetex

/.
/usr/
/usr/share
...
[127 lines ending with /usr/bin/xelatex]
```

Thanks for any help.


s.b.

---

### Post by hugmenot on 2009-08-15
Wrong command. XeTeX is an /alternative/ to pdfTeX.
To process use xelatex not pdflatex.

---

