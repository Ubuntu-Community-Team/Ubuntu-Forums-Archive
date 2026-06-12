---
title: "Latex: latex2E can't find files... texhash doesn't fix"
date: 2009-08-03
forum: General Help
---

### Post by washakie on 2009-08-03
Hello,

I have installed latex and texlive*, now I've been trying to get latex to work from the command line, but I repeatedly get the error:

! LaTeX Error: File `letter.cls' not found.

Or basically any file I try to use that is not in the directory. It does work if I explicitly copy the file to the working directory, but this really seems a poor solution... creating so many duplicates (or perhaps links)...

I have run texhash both as sudo and as my user (though then I do get permission errors if I run it with no arguments as my user alone). I have run texhash inside my $HOME/texmf directory as:

$texhash *

and even individually for each subdirectory.

I also have set my TEXINPUTS shell variable. All this, with no success of getting latex to work from the command line, which in turn means I cannot use the vim-latex suite (ie. \ll) to compile my documents. 

Any ideas?! This is maddening. 

One further note. Everything works fine in Kile.

Thanks!

SOLUTION:

FOUND MY OWN WAY... a few minutes after posting I found this:
[http://myitcv.org.uk/latex/tips_and_tricks.html#answer9](http://myitcv.org.uk/latex/tips_and_tricks.html#answer9)

The solution was to include the '//' for recursive addition of the TEXINPUT var. Also, note, it's import to include '.' on your path. So in the end I have:

#TEX
TEXINPUTS=.:~/texmf/tex/latex//:/usr/share/texmf-texlive//
export TEXINPUTS
BIBINPUTS=.:~/texmf/tex/bibtex//:/usr/share/texmf-texlive/tex/bibtex//
export BIBINPUTS
BSTINPUTS=${BIBINPUTS}
export BSTINPUTS

---

