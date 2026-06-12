---
title: "Cannot make gedit latex plugin to build image"
date: 2009-11-17
forum: General Help
---

### Post by infestor on 2009-11-17
this function simply does not work with me! i can build pdfs with the plugin but not image. anyone has any solution to that?

---

### Post by infestor on 2009-11-17
i also constantly get depreciation error (see attached image)

---

### Post by snizovtsev on 2009-11-21
[SIZE=4]Workaround:[/SIZE]
open /usr/bin/rubber and change content like this:
```

#!/usr/bin/python
# This is just a wrapper script for the main Python program
# This script is part of Rubber, which is covered by the GPL license.
# (c) Emmanuel Beffara, 2002
import sys
[COLOR=Green]import warnings[/COLOR][COLOR=Green]
warnings.filterwarnings('ignore')
[/COLOR] 
sys.path.append("/usr/share/rubber")
try:
    from rubber.cmdline import Main
    sys.exit(Main()(sys.argv[1:]))
except ImportError:
    print "I cannot find the program's modules, I am not installed correctly."
    sys.exit(1)

```
P.S. Unfortunately, i have found another annoying bugs:
1. Embedded preview doesn't handle russian characters
2. "Choose master document" doesn't work

---

### Post by infestor on 2009-11-22
i have moved to kile, gedit latex plugin is just a mistake itself.

---

### Post by XCan on 2009-11-23
Although I didn't know the solution of your problem, I find the default build profiles using rubber in the plugin very inconvenient and buggy. Thus I have trashed the default build profiles in favor of the standard latex; latex; dvipdf; builds. Or the pdflatex equivalents obviously.

---

### Post by yanv on 2010-04-24
Hi XCan,
May I ask you why you find the default profiles buggy and inconvenient ? I am involved in the development some parts of the plugin, and I would be interested to know about this kind of problems.
Thanks!

---

### Post by yanv on 2010-04-24
Hi snizovtsev,
If it still doesn't work, could I ask you to paste here some code with russian characters and  which doesn't render correctly in the preview ? Thank you.

---

### Post by kkloster on 2010-05-03
@yanv:

i've been having trouble using rubber with the gedit-latex-plugin also.  i call the graphicx and epstopdf packages in my .tex files to convert .eps files to .pdf on the fly.  When i use rubber as the postprocessor for the gedit-latex-plugin, none of the .eps image files are converted to .pdf image files and the pdf document is not created.  If i change the post processor to pdflatex then .eps figures are properly converted to .pdf figures and the pdf document is built fine (but then bibtex stuff isn't taken care of automatically like it is in rubber).

i originally thought it was a problem with shell escape not being enabled when calling pdflatex through rubber (and that may in fact be the problem) but i tried using "-m pdflatex:shell-escape" and a bunch of variations on that and it didn't work.

i'd like to be able to use rubber with the gedit-latex-plugin but i can't get around this.

I am using the default rubber command and flags:

```
rubber --inplace --maxerr -1 --short --force --warn all --pdf "$filename"
```

are there any flags i can use that will solve this problem?

---

### Post by yanv on 2010-05-04
Hi kkloster,

Rubber was coded to automatically convert eps files to pdf when compiling to pdf (with using the epstopdf package, by calling the epstopdf executable). However, this feature doesn't seem to be working anymore lately
I don't really understand why it is so, it seems that the epstopdf executable realy needs to be called from a shell...
A workaround for this is to replace line 86 of /usr/share/rubber/rules.ini (with root priileges)

command = epstopdf --outfile=$target $source

by

command = bash epstopdf --outfile=$target $source

This is however not optimal, since rubber normally checks for the existence of the program before running it, and it will nowonly check for the existence of "bash"... 

Could you tell me if it works for you ? 
And if it doesn't, could you run rubber on your file in a terminal (with a command "rubber --pdf your_file.tex") and post the output, as well a the output from trying to compile using rubber through gedit (also started from a terminal) ?

I will also post a bug report on the rubber dev page on launchpad so that hopefully a better fix can be found.

Yannick

---

### Post by yanv on 2010-05-04
> **yanv said:**
> Rubber was coded to automatically convert eps files to pdf when compiling to pdf (with using the epstopdf package, by calling the epstopdf executable)
I meant: _without_ using the epstopdf package! Rubber will convert the eps to pdf before running pdflatex, so that if the epstopdf package is used, it will simply not have to do anything (but will not crash or make the compilation fail).

---

### Post by kkloster on 2010-05-04
@yanv:

it works perfectly after making the change to line 86 as you suggested.

thanks!

if i can help you debug this issue further, don't hesitate to give me some things to try - i can post error messages here for you.

i guess i should mention, just to be clear, when i would run rubber through gedit before i applied your fix, it wasn't producing any output files at all (i.e., no log file or aux file or anything). maybe it was checking for epstopdf and not finding it (even though it really is there)?

thanks again.

---

