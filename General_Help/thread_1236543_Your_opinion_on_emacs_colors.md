---
title: "Your opinion on emacs colors"
date: 2009-08-10
forum: General Help
---

### Post by d0.higgs on 2009-08-10
Hi,
I have never been good with colors. I mean I can't match them together!
I have compiled my .emacs file from scratch, and I wish if you can tell me your opinions about the colors. I want something that's very easy to my eyes as I am/will spend a lot of time with emacs.
Here is my .emacs file:
```
(custom-set-faces
  ;; custom-set-faces was added by Custom.
  ;; If you edit it by hand, you could mess it up, so be careful.
  ;; Your init file should contain only one such instance.
  ;; If there is more than one, they won't work right.
 '(default ((t (:inherit nil :stipple nil :background "LightBlue1" :foreground "black" :inverse-video nil :box nil :strike-through nil :overline nil :underline nil :slant normal :weight regular :height 122 :width regular :foundry "bitstream" :family "Bitstream Vera Sans")))))

;;save everything to a folder
(setq backup-by-copying t ; don't clobber symlinks
backup-directory-alist
'(("." . "~/emacs_backup")) ; don't litter my fs tree
delete-old-versions t
kept-new-versionhs 6
kept-old-versions 2
version-control t) ; use versioned backups

(setq default-frame-alist '(
(cursor-color . "saddle brown")
(user-position . t)
(user-size . t)
(height . 40)
(width . 100)))

(set-face-foreground 'font-lock-variable-name-face "chocolate4" )
(set-variable font-lock-variable-name-face 'font-lock-variable-name-face)

(set-face-foreground 'font-lock-type-face "dark green" )
(set-variable font-lock-type-face 'font-lock-type-face)

(set-face-foreground 'font-lock-comment-face "thistle4" )
(set-variable font-lock-comment-face 'font-lock-comment-face)

(set-face-foreground 'font-lock-string-face "firebrick" )
(set-variable font-lock-string-face 'font-lock-string-face)

(set-face-foreground 'font-lock-preprocessor-face "sandy brown" )
(set-variable font-lock-preprocessor-face 'font-lock-preprocessor-face)

(set-face-foreground 'font-lock-constant-face "green4" )
(set-variable font-lock-constant-face 'font-lock-constant-face)

(set-face-foreground 'font-lock-keyword-face "blue1" )
(set-variable font-lock-keyword-face 'font-lock-keyword-face)

(set-face-foreground 'font-lock-function-name-face "blue violet" )
(set-variable font-lock-function-name-face 'font-lock-function-name-face)
```

If you have any suggestions or ideas, I will be grateful.

**Notice, backup your .emacs file before you try mine.**

Thanks in advance,

d0.higgs

---

