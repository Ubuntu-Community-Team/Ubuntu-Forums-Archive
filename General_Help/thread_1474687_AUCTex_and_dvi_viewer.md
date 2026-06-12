---
title: "AUCTex and dvi viewer"
date: 2010-05-06
forum: General Help
---

### Post by miguelastico on 2010-05-06
Hi, I am using emacs+auctex for latex editing
now, I want to change the default viewer for dvi files, since xdvi doesn't render correctly most of my documents; okular works perfectly, though I cannot make it the default viewer
I went into the AUCTex manual, and there is a tex-view-program list that should contain the list of viewers, but I cannot find the way to customize that variable
anybody has an idea about how I can solve?
Thanks,
Michele

---

### Post by fbkarsdorp on 2010-05-21
Hi, try adding this to your .emacs file:

(defun dvi-with-okular ()
   (add-to-list 'TeX-output-view-style 
                    (quote ("^dvi$" "." "okular %o %(outpage)"))))

(add-hook 'LaTeX-mode-hook 'dvi-with-okular t)

---

### Post by miguelastico on 2010-05-21
Hi,
Thanks.
At the end I did it changing the TeX-output-view-style from the "customize AUCTeX" menu entry. I just changed any reference to xdvi to okular. Now I have other two goals:
1 - I would like to change the latex command in latex + dvi2pdf and the view to acrobat reader (okular doesn't manage my beamer presentations), right now I am issuing the print command after latex, and then I am opening the file manually
2 - inverse search from the dvi to the emacs buffer...
Any suggestion is welcome, even though I think they are worth at least another post :)

---

### Post by fbkarsdorp on 2010-05-22
Hi, 

this is for viewing pdf with adobe:

(defun pdfadobe ()
   (add-to-list 'TeX-output-view-style
                    (quote ("^pdf$" "." "acroread %o %(outpage)"))))

(add-hook 'LaTeX-mode-hook 'pdfadobe t)

For the inverse dvi search, check this site:

[http://www.emacswiki.org/emacs/InverseDviSearch](http://www.emacswiki.org/emacs/InverseDviSearch)

---

### Post by miguelastico on 2010-05-22
Thanks for the help.
I can put it in .emacs and it doesn't give any error, but I don't know how to use it :)
I put it after all the other commands, so that it shouldn't give problems, but no luck for now, I will document myself more and see how I can make it work.
However, I don't know if I want to have always the pdf view, since I think it will cancel the possibility of having inverse search from the dvi. I think I will stick with the print command.
Thanks for everything.

---

### Post by jiapeng on 2010-07-18
> **fbkarsdorp said:**
> Hi, try adding this to your .emacs file:

(defun dvi-with-okular ()
   (add-to-list 'TeX-output-view-style 
                    (quote ("^dvi$" "." "okular %o %(outpage)"))))

(add-hook 'LaTeX-mode-hook 'dvi-with-okular t)


Really good method for WYSWIG LaTeX editing.  And, I want to know, is  there way to produce .dvi file first and then use 'dvipdf' command to produce pdf in Emacs? 
:KS

---

### Post by miguelastico on 2010-07-19
> **jiapeng said:**
> Really good method for WYSWIG LaTeX editing.  And, I want to know, is  there way to produce .dvi file first and then use 'dvipdf' command to produce pdf in Emacs? 
:KS

The dvi file is produced by the Latex command (C-c C-c RET) and I modified the print command in order to use dvipdf as printer. I do not remember how I did it, but I will let you know as soon as I get back to my machine, unless someone doesn't post it before

---

