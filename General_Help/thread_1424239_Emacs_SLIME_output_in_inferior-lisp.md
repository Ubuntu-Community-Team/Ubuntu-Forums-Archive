---
title: "Emacs SLIME output in inferior-lisp"
date: 2010-03-07
forum: General Help
---

### Post by radiancia on 2010-03-07
I need help solving a problem I have been unable to find a solution for anywhere.

I am trying to learn Common Lisp, so I installed Emacs 22.2.1 and SLIME. However, I have been unsuccessful using Lisp's 'format' function. The *value of each expression* is shown in the *slime-repl clisp* buffer, as expected, but the *output of the 'format' function* is always put in the *inferior-lisp* buffer, not the *slime-repl clisp* buffer like I expected. How can make all output, including that of the 'format' function, go to the *slime-repl clisp* buffer?  (Please look at the screenshot if my question is unclear.)

Background information:
I am using the Linux Mint 8 main edition (a derivative of Ubuntu; no one responded in their forums). I installed the 'emacs', 'slime', and 'clisp' packages using Synaptic. Afterward, I created an empty .slime folder as suggested here <[http://www.osix.net/modules/article/?id=912](http://www.osix.net/modules/article/?id=912)> and a .emacs file (shown below) in my home directory.

My .emacs file:
```
;;; Load path
(add-to-list 'load-path "~/emacs/site-lisp")
(add-to-list 'load-path "~/emacs/lisp")

;;; Lisp (SLIME) interaction
(setq inferior-lisp-program "clisp -K full")
(add-to-list 'load-path "~/.slime")
(require 'slime)
(slime-setup)

;;; Automatic syntax highlighting
(global-font-lock-mode t)

;;; Match parentheses
(show-paren-mode 1)

;;; Correctly indent lisp code
;;; (add-hook 'lisp-mode-hook '(lambda ()
;;;    (local-set-key (kbd "RET") 'newline-and-indent)))

;;; Transient mark mode
(transient-mark-mode)

;;; Autoindent
(define-key global-map (kbd "RET") 'newline-and-indent)
(add-hook 'f90-mode-hook
  (lambda () (local-set-key (kbd "RET") 'reindent-then-newline-and-indent)))
```Screenshot of the issue:
[IMG]http://farm5.static.flickr.com/4033/4317074437_c261150db2_o.png[/IMG]

Thanks in advance for your help!

---

### Post by radiancia on 2010-03-09
I found a solution at <[http://common-lisp.net/pipermail/slime-devel/2009-May/016223.html](http://common-lisp.net/pipermail/slime-devel/2009-May/016223.html)>.

If anyone has this problem in the future, the fix is to add the line ```
(setq SWANK:*GLOBALLY-REDIRECT-IO* t)
``` to the .swank.lisp file in your home directory (create the file if it doesn't yet exist).

---

### Post by SZVSZ on 2010-06-22
Thanks so much for posting this tip, radiancia! :KS :KS :KS
I was having the same problem.

---

### Post by radiancia on 2010-06-23
I'm glad I could help.  Thanks for your reply!  It is nice to know that I helped someone.

---

