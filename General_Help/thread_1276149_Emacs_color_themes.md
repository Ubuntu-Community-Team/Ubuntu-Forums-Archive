---
title: "Emacs color themes"
date: 2009-09-26
forum: General Help
---

### Post by dmsynck on 2009-09-26
Hi all,

Just starting out with GNU Emacs and Emacs-lisp. I am trying to get a color scheme I like for Emacs, so I installed the emacs-goodies package from the repos and added the following code to my .emacs file as noted from the "Emacs wiki" webpage.

```
(add-to-list 'load-path "/usr/share/emacs/site-lisp/emacs-goodies-el/")
(require 'color-theme)
(eval-after-load "color-theme"
  '(progn
     (color-theme-initialize)
     (color-theme-Katester)))
```

When I evaluate my .emacs file, I get the following error

Loading /home/dms/.emacs...
progn: Symbol's function definition is void: color-theme-initialize

Anybody have any ideas ?

Thanks in advance,

DMSynck

---

### Post by fabian.r on 2009-10-16
Hi dmsynck,

You have marked the thread as "[SOLVED]".
I think I have got the same problem as you had.

Could you please post your solution here?

Thanks in advance,
Fabian

---

### Post by jpkotta on 2009-10-17
Emacs is saying that the function is undefined.  If you M-x find-library RET color-theme RET and search for color-theme-initialize, you won't find anything.  It works for me if I just remove the line.  Also, it's color-theme-katester, not color-theme-Katester.  And I don't think the eval-after-load is necessary either.  require loads the library anyway, so it will be loaded after that line.

```
(require 'color-theme)
(color-theme-katester)
```

---

### Post by miguelastico on 2010-01-23
that solved for me as well, thanks

---

