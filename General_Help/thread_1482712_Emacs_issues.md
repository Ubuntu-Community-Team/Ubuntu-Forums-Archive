---
title: "Emacs issues"
date: 2010-05-13
forum: General Help
---

### Post by jhapk on 2010-05-13
Hi,

everytime I launch my emacs I get this line on my command line.
```

(emacs:4174): GLib-WARNING **: g_set_prgname() called multiple times

```And also, I use a .emacs file at my work for fedora 12 and when I use the exact same .emacs at home for ubuntu, I find that all my colour code for c++, latex or any other language in emacs disappears and all the text is displayed only in white colour.

Any clues whats going wrong?

My .emacs looks like this
```

;; --------
;; REQUIRES
;; --------

;; common-lisp
(require 'cl)
;; match parentheses
(require 'paren)

;; inhibit startup message
(setq inhibit-startup-message t)

;;-----------------------------------------------------
;; wait zero seconds before changing frame parameters
;;-----------------------------------------------------
(modify-frame-parameters nil '((wait-for-wm . nil)))

;;------------------------
;;General window settings
;;------------------------

(set-face-background 'default "black")
(set-face-foreground 'default "white")
(global-font-lock-mode)
(setq column-number-mode t)
(custom-set-variables
  ;; custom-set-variables was added by Custom -- don't edit or cut/paste it!
  ;; Your init file should contain only one such instance.
 '(case-fold-search t)
 '(current-language-environment "Latin-1")
 '(default-input-method "latin-1-prefix"))
;; display date and time always
;;(setq display-time-day-and-date t)
;;(display-time)

(custom-set-faces
  ;; custom-set-faces was added by Custom -- don't edit or cut/paste it!
  ;; Your init file should contain only one such instance.
 '(font-lock-comment-face ((((class color) (background dark)) (:foreground "red"))))
 '(font-lock-keyword-face ((((class color) (background dark)) (:foreground "green"))))
 '(font-lock-string-face ((((class color) (background dark)) (:foreground "orange"))))
 '(font-lock-type-face ((((class color) (background dark)) (:foreground "deep sky blue"))))
 '(font-lock-variable-name-face ((((class color) (background dark)) (:foreground "deep pink"))))
 '(font-lock-function-name-face ((((class color) (background dark)) (:foreground "peach puff")))))

;; enable transient-mark-mode!  HOORAY!
(setq-default transient-mark-mode t)

; saving the buffer list
(load "desktop")
(desktop-load-default)
(desktop-read)

;; window size
(setq initial-frame-alist '((width . 161) (height . 70)))

;; dissable tool-bar
(tool-bar-mode nil)

;;C++ specific
(which-function-mode t)       ;; In source code, try to show curr func name

;;;;;;;;;;;;;;;;
;;  .in mode  ;;
;;;;;;;;;;;;;;;;
(add-to-list 'auto-mode-alist '("\\.in\\'" . sh-mode))
;;(add-to-list 'auto-mode-alist '("\\.in\\'" . makefile-mode))

;;;;;;;;;;;;;;;;
;; .def mode  ;;
;;;;;;;;;;;;;;;;
(add-to-list 'auto-mode-alist '("\\.def\\'" . makefile-mode))

;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;  Global key bindings  ;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;
(global-set-key "\C-g" 'goto-line)
(global-set-key [(control prior)] 'bury-buffer)        ;; Ctrl-PgUp for previous buffer
(global-set-key [(meta left)] 'backward-sexp)        ;; find matching start brace
(global-set-key [(meta right)] 'forward-sexp)        ;; find matching end brace
(global-set-key [(f5)] 'undo)
(global-set-key "\C-b" 'switch-to-buffer)
(global-set-key "\C-v" 'toggle-truncate-lines)
(global-set-key "\C-p" 'show-paren-mode)                ;; show matching braces
(global-set-key "\C-z" nil)                             ;; deactivate ctrl+z 
(global-set-key "\C-f" 'ediff)                          ;; diff files
(global-set-key "\C-k" 'ispell)                         ;; spell check

;; multiple shells
(defun my-shell (arg)
  (interactive "p")
  (let ((arg (or arg 1)))
    (shell (format "*sh%d*" arg))))

(global-set-key [f1] '(lambda () (interactive) (my-shell 1)))
(global-set-key [f2] '(lambda () (interactive) (my-shell 2)))
(global-set-key [f3] '(lambda () (interactive) (my-shell 3)))
(global-set-key [f4] '(lambda () (interactive) (my-shell 4)))
(global-set-key [f5] '(lambda () (interactive) (my-shell 5)))

;;; Fix junk characters in shell mode
(add-hook 'shell-mode-hook
         'ansi-color-for-comint-mode-on)

;; no delay while locating matching braces
(setq show-paren-delay 0)

;;-----------------------
;; set default font
;;-----------------------
(set-default-font "-adobe-courier-medium-r-normal--18-180-75-75-m-110-iso8859-1")


;; type "y"/"n" instead of "yes"/"no"
(fset 'yes-or-no-p 'y-or-n-p)

;; C-k kills whole line and newline if at beginning of line
(setq kill-whole-line t)

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;  increasing/decreasing font size from keyboard  ;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
(defun pradeep/increase-font-size ()
  (interactive)
  (set-face-attribute 'default
                      nil
                      :height
                      (ceiling (* 2.00
                                  (face-attribute 'default :height)))))
(defun pradeep/decrease-font-size ()
  (interactive)
  (set-face-attribute 'default
                      nil
                      :height
                      (floor (* 0.5
                                  (face-attribute 'default :height)))))
(global-set-key (kbd "C-+") 'pradeep/increase-font-size)
(global-set-key (kbd "C--") 'pradeep/decrease-font-size)

(defadvice save-buffers-kill-emacs (around no-query-kill-emacs activate)
  "Prevent annoying \"Active processes exist\" query when you quit Emacs."
  (flet ((process-list ())) ad-do-it))


;; Shell mode
(setq ansi-color-names-vector ; better contrast colors
      ["black" "red4" "green4" "yellow4"
       "red3" "magenta4" "cyan4" "white"])
(add-hook 'shell-mode-hook 'ansi-color-for-comint-mode-on)
(setq comint-scroll-to-bottom-on-input t) ;; scroll to botton on input
(setq comint-scroll-to-bottom-on-output t) ;; scroll to botton on output
(setq comint-input-ignoredups t) ;; don't store consecutive identical inputs in history
(setq comint-scroll-show-maximum-output t) ;; place the last line of output at the bottom line of the window

;; count the number of words in buffer
(defun word-count nil "Count words in buffer" (interactive)
  (shell-command-on-region (point-min) (point-max) "wc -w"))
(global-set-key (kbd "C-o") 'word-count)

```

---

### Post by jpkotta on 2010-05-15
Try replacing (global-font-lock-mode) with (global-font-lock-mode 1).  With no argument, it toggles the setting, with an arg > 0, it enables the mode.

---

### Post by jhapk on 2010-05-15
Hi,

thanks. That solved the font colour issue for me. Any clues why I get the message

```
(emacs:4174): GLib-WARNING **: g_set_prgname() called multiple times
```everytime I launch emacs?

---

### Post by jpkotta on 2010-05-15
Whenever you have an error message like that, a good first step is to just paste it into Google.  Apparently it happens for several applications and should be fixed for emacs on 10.04.

[https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/501670](https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/501670)

In any case, if it isn't causing you immediate problems, submit a bug report and ignore it.

---

### Post by jhapk on 2010-05-15
thanks for the reply. I did google it and found that many applications had this issue. but couldn't find a solution, that why I posted it.

---

