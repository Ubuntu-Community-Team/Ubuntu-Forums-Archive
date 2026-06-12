---
title: "Is there really no linux text editor with smart line wrapping?"
date: 2011-09-23
forum: General Help
---

### Post by jatoo on 2011-09-23
Hi all,

I'm looking for a linux text editor (in this case for Latex, but just in general) which has smart line wrapping (soft line wrapping).

i.e., does this:
```

\subsection{My subsection}
        Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nunc
        congue dui nec purus semper id egestas mi ullamcorper.

```


and not this:
```

\subsection{My subsection}
        Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nunc
congue dui nec purus semper id egestas mi ullamcorper.

```

I have tried: Kile, vim, emacs, nano and gedit.

The only thing i've found which actually does it so far is Notepad++, but i need to run that under wine (which isn't as nice as running a native app).

Any suggestions?

---

### Post by raja.genupula on 2011-09-23
[http://geekhack.org/showthread.php?4977-any-linux-text-editors-that-do-an-auto-word-wrap-sorta-thing](http://geekhack.org/showthread.php?4977-any-linux-text-editors-that-do-an-auto-word-wrap-sorta-thing)

---

### Post by jpkotta on 2011-09-25
In Emacs, you can try this:
```

(defun srb-adaptive-indent (beg end)
  "Indent the region between BEG and END with adaptive filling."
  (goto-char beg)
  (while
      (let ((lbp (line-beginning-position))
            (lep (line-end-position)))
        (put-text-property lbp lep 'wrap-prefix (fill-context-prefix lbp lep))
        (search-forward "\n" end t))))

(define-minor-mode srb-adaptive-wrap-mode
  "Wrap the buffer text with adaptive filling."
  :lighter ""
  (save-excursion
    (save-restriction
      (widen)
      (let ((buffer-undo-list t)
            (inhibit-read-only t)
            (mod (buffer-modified-p)))
        (if srb-adaptive-wrap-mode
            (progn
              (setq word-wrap t)
              (unless (member '(continuation) fringe-indicator-alist)
                (push '(continuation) fringe-indicator-alist))
              (jit-lock-register 'srb-adaptive-indent))
          (jit-lock-unregister 'srb-adaptive-indent)
          (remove-text-properties (point-min) (point-max) '(wrap-prefix pref))
          (setq fringe-indicator-alist
                (delete '(continuation) fringe-indicator-alist))
          (setq word-wrap nil))
        (restore-buffer-modified-p mod)))))

```

I tried it in a text buffer with visual-line-mode on, and it seemed to do exactly what you want.  Plus you can use it with AUCTeX!

Source: [http://www.emacswiki.org/emacs/LineWrap](http://www.emacswiki.org/emacs/LineWrap)

---

### Post by staticd on 2011-09-25
I use** geany** to edit both programs and tex. The line wrapping( Document->Line wrapping) is exactly how you want it. the integrated build/ run buttons are very convenient. You should also install the texlive plugins for geany. all available through synaptic.

---

### Post by ilovelinux33467 on 2011-09-25
Kate can also do this with its Dynamic Word Wrap feature (Settings -> Configure Kate -> Editor Component -> Appearance and tick "Dynamic Word Wrap" box.)

---

