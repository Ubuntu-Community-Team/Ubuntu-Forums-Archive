---
title: "Customize AUCTeX view command in Emacs"
date: 2010-05-20
forum: General Help
---

### Post by artursm on 2010-05-20
I've been using Emacs with the AUCTeX package to edit and compile my .tex documents lately, but there's something that's been bugging me. First, here is the short question:

**How can I costumize the default view command emacs runs when I type *C^c C^c <enter>*?**
I've read that it's done with the *tex-view-dvi-command* variable, but I've had no luck getting it to work at all.

Now the explanation:
It bugs me that whenever I type *C^c C^c* to compile, and then *C^c C^c* to view dvi, emacs doesn't automatically give focus to the dvi viewer (xdvi). Digging a little, I found out that the command "*wmctrl -a main*" gives focus to xdvi ("main" is the title of the xdvi window). So, if I can only customize AUCTeX's standard view command to include "*&& wmctrl -a main*" at the end, than my problem would be solved.
[SIZE="1"]
In case it matters, I'm running Lucid Lynx, and emacs runs on Latex mode with source-specials, folding, and references (LaTeX/FS Ref).[/SIZE]

---

### Post by artursm on 2010-05-20
Ok, I believe I found a way, but it feels kinda clunky, so feel free to suggest a better way.

The default view command is composed by "xdvi", followed by a few arguments defined by some variables, followed by the file name. The last argument before the file name is defined by the variable "Tex Source Specials View Editor Flags", and its default value is: "-editor "%cS"" (without the outermost quotes). 

I added "%d && wmctrl -a `echo %d | sed -e 's/.dvi//g'` #" to the end of this variable. Remember that this is the last argument in the view command before the filename. 
 %d is meant to replace the filename.
 && ends the xdvi (view) command.
 wmctrl -a will give focus to the window titled: `echo %d | sed -e 's/.dvi//g'` (which is the name of the dvi file without the .dvi extension).
 # at last, just tells bash to ignore whatever comes next. In our case, that's the filename that emacs automatically appends after all of this.

---

### Post by jpkotta on 2010-05-20
Look in section 7.2 "Viewing the formatted output" of the AUCTeX manual.  In particular, it looks like you want TeX-output-view-style and TeX-view-style, not tex-view-dvi-command.  These look like particularly complicated variables -- I'd set them using M-x customize-variable.  I use AUCTeX but not this particular feature, because I usually use a makefile to build the document and a PDF viewer (okular) that is smart enough to refresh when the PDF file is updated.

---

