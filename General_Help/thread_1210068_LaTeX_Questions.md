---
title: "LaTeX Questions"
date: 2009-07-11
forum: General Help
---

### Post by colsandurz on 2009-07-11
I have written a good amount of latex documents (> 15), yet I always seem to struggle with the same few things...

The first is letterpaper, I can never get my documents to come out in letterpaper (as opposed to A4) without some great struggle.

The second is installing latex, texlive, etc.  apt-get always wants me to install all these language packs and things I don't need making the download 600 MB or more

The third is outlines.sty from, I think, \usepackage{outlines} I have a friend who uses this package all the time and my machine can never find outlines.sty!

The fourth is margins.  Sometimes make the margins and they look fine in the dvi, but when I convert to ps or pdf everything goes to hell.  Like the writing will go off the page or the left margin will be different than the right.

Does anyone share these frustrations?  If so, could you solve them?  My solutions to these always seem like ugly hacks (like downloading an outlines.sty file from the internet and dropping it in the directory I'm compiling in).  So I'm really looking for solutions that are more elegant.

Thanks!

---

### Post by Chronon on 2009-07-11
1) Most document classes I have used accept papersize as an optional parameter.  Otherwise you can use the "geometry" package to set custom margins, page size, etc.

*Actually, I am having this too, as it turns out.  I have tried a number of things but it seems that TexLive always wants to default to A4.  I invoked the geometry package and explicitly set the page height and width but the resulting document (PDF after running dvipdf on the .dvi) still has A4 page size.  My school/work computer runs Windows and has MikTex installed on it.  The document builds fine with US Letter page size in that environment.*

===========
EDIT:
**I found the solution.  You need to run "texconfig paper letter" to change the default to letter.  I would have thought that invoking a package like geometry should override the default behavior.  Anyway, my pages are now US-Letter rather than A4.**
===========

2) Everything is kind of bundled in Ubuntu so I can't really offer any solution here.  I hear the TexLive 2008 has a package manager that allows installation of individual LaTeX packages.  

By the way, it is possible to manually install packages.  See here: [https://help.ubuntu.com/community/LaTeX#Installing](https://help.ubuntu.com/community/LaTeX#Installing) packages manually

3) I'm not sure if it's the same package or not, but "outline.sty" is in texlive-latex-extra.

4) I don't usually have problems like this.  Sometimes it seems that the compiler gets confused and stacks things up in a weird way.  I usually just try to reposition calls to floating environments and such things to try to fix that.  My margins are generally fine.

---

### Post by colsandurz on 2009-07-11
thanks a lot.... the texconfig paper letter command was especially helpful.

---

### Post by grappler on 2009-07-11
As a result of your question, I searched in synaptic for texlive and found a collection of separate language packages that I'd installed without thinking. I found I could delete all of these provided I also deleted a package called tetex-extra. To quote from its description:

> This is a transitional package to bring former teTeX users a
decent selection of TeX Live packages.  It can be safely removed (unless
some external packages still depend on tetex-extra).Deleting these packages saved me 63MB.

---

### Post by grappler on 2009-07-11
There is an outlines.sty - as well as outline.sty and outliner.sty - confusing! It is at:

[http://www.info.ucl.ac.be/~pecheur/soft/outlines.sty](http://www.info.ucl.ac.be/~pecheur/soft/outlines.sty)

Just downloaded and put in my local tex directory 
(in my case /usr/local/share/texmf) and run texhash:

```
sudo texhash
```

 Make sure that the directory is part of of your TEXINPUTS variable

TEXINPUTS=$TEXINPUTS:/usr/local/share/texmf//:

I still have to work out what it does but when I run pdflatex over a file with 
\usepackage{outlines} in it it finds it.

---

### Post by grappler on 2009-07-11
One final comment. I've given up going through .dvi - just run pdflatex on the original tex file to produce the pdf file.  I don't see the advantages in using tex-> .dvi -> .ps -> .pdf any longer.  The only issue is to make sure that images conform to the requirements for pdflatex - which means one of .pdf, .jpg. .png and I think several others - but not .eps. 

Also you cannot use pstricks I think. There is an alternative pgf/tikz. It's not quite as flexible as pstricks but I've never had a problem with it.

---

### Post by XCan on 2009-07-11
> **grappler said:**
> One final comment. I've given up going through .dvi - just run pdflatex on the original tex file to produce the pdf file.  I don't see the advantages in using tex-> .dvi -> .ps -> .pdf any longer.  The only issue is to make sure that images conform to the requirements for pdflatex - which means one of .pdf, .jpg. .png and I think several others - but not .eps. 

Also you cannot use pstricks I think. There is an alternative pgf/tikz. It's not quite as flexible as pstricks but I've never had a problem with it.

I never quite understood the purpose of .dvi ever since .pdf got 'invented'. Especially considering how lousy performance are in all the viewers.

---

### Post by grappler on 2009-07-11
The only reason I've found to continue to use .dvi is that there is an "instant" way to generate .dvi files using whizzytex but it is troublesome to set up and I've never felt it was worth the effort. People who need wysisyg lack imagination! ;)

---

### Post by spibou on 2009-07-11
> **XCan said:**
> I never quite understood the purpose of .dvi ever since .pdf got 'invented'. Especially considering how lousy performance are in all the viewers.
I use xdvi for DVI files and I've never had any performance problems. On the other hand xpdf with some files takes several seconds to move between pages. But I keep using it because it's the only xpdf viewer I know which allows you to change the background colour.

---

### Post by Chronon on 2009-07-12
I have been using dvipdf to convert DVI --> PDF.  I already have a lot of graphics for my current document in .eps format, so pdflatex is not an option for me presently.

---

### Post by grappler on 2009-07-12
Just discovered epstopdf.sty which converts eps to pdf automatically when running pdflatex.

[http://www.koders.com/noncode/fid82F897967530D00D13E9D7C0188AB4BF8C4B77ED.aspx](http://www.koders.com/noncode/fid82F897967530D00D13E9D7C0188AB4BF8C4B77ED.aspx)

---

