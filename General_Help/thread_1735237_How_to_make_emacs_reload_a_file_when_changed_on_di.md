---
title: "How to make emacs reload a file when changed on disk?"
date: 2011-04-21
forum: General Help
---

### Post by TheHimself on 2011-04-21
I've noticed that emacs does not notice when an open file is changed on disk (unlike ,say, geany). Is there any way of making it watch for changes of files on disk?

---

### Post by jpkotta on 2011-04-23
See [http://www.gnu.org/software/emacs/manual/html_node/emacs/Reverting.html](http://www.gnu.org/software/emacs/manual/html_node/emacs/Reverting.html)

I have this in my init.el:

```

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;; revert

(global-auto-revert-mode 1)
(setq auto-revert-verbose nil)

(global-set-key (kbd "<f5>") 'revert-buffer)

```

---

