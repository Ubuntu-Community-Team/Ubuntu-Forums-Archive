---
title: "Latex syntax using Flymake: Emacs"
date: 2011-01-29
forum: General Help
---

### Post by yaami on 2011-01-29
Hi all,
I'm trying to use emacs in the auctex mode. But Flymake complains about
something I could not understand. This is the error it shows whenever I
open a tex file.

```
Flymake:Configuration error has occured while running (texify --pdf --tex-option=-c-style-errors PATH_TO_FILE_DIRECTORY/FILE_flymake.tex).
Flymake will be switched OFF.
```

I have texify installed on my system. I also tried suggestions in the
emacs wiki on FlymakeTex, added the following lines in my .emacs file:

```
(defun flymake-get-tex-args (file-name)
  (list "pdflatex" (list "-file-line-error" "-draftmode"
"-interaction=nonstopmode" file-name)))
```

But this does not help. How do I stop this msg and use flymake. 

Thanks,

---

### Post by aamikkelsen on 2011-05-17
I have the same problem...

---

### Post by Jorge_C on 2012-05-20
This arrives a bit late, but I just ran into this issue. Google didn't help this time but I found a workaround.

It turns out the folder I had my tex file in had a backslash in its name. I removed it, and now everything works fine.

I also added
```
(defun flymake-get-tex-args (file-name)
    (list "pdflatex" (list "-file-line-error" "-draftmode" "-interaction=nonstopmode" file-name)))
```
to .emacs, as suggested in the [emacs wiki]("http://www.emacswiki.org/emacs/FlymakeTex")

---

