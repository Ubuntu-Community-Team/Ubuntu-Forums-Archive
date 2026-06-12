---
title: "Key bindings suddenly changed in Emacs"
date: 2010-02-22
forum: General Help
---

### Post by sinbadbuddha on 2010-02-22
So, I turn on my laptop running 64-bit karmic (if that helps anyone), open GNU Emacs 23.1.1 with the org files I've been working on, and for some reason it is not recognising standard key bindings, for the first time ever, with no reason I can conceive.
What does "M-kp-enter is undefined" mean when it seemed well defined not long before? It seems using Esc-enter still works.. can anyone suggest if there are any config files I might need to edit, or what else could have gone wrong?

---

### Post by jpkotta on 2010-02-26
You can bypass your config files with ```
emacs -q
``` and all third-party config files (including yours) with ```
emacs -Q
```.   If the problem goes away with those options, you've narrowed it down.

You can also bind a key in org-mode-hook (probably, I don't use org-mode).  
```

(defun my-org-mode-hook ()
  (local-set-key (kbd "M-<kp-enter>") 'some-command))

(add-hook 'org-mode-hook 'my-org-mode-hook)

```

---

