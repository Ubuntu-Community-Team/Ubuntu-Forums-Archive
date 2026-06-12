---
title: "Continuous document viewing in Emacs"
date: 2009-07-31
forum: General Help
---

### Post by Bluebottel on 2009-07-31
I want to be able to split the Emacs window vertically and still read the same document.
If window #1 show line 1, 2 and 3 i want window #2 to show line 3, 4, 5 etc.
I can split the window vertically without problems (C-x 3) but it wont automatically scroll for me.
It would alse be great if the solution could be expanded to even more windows such as window #1 show line 1, 2, 3 window #2 line 4, 5, 6 and window #3 line 7, 8, 9.

I intend to use it on my netbook to maximise the use of the wide, but not all that tall screen.

Thanks in advance.

---

### Post by Bluebottel on 2009-08-03
I have done my homework and solved this "problem". Here's how to do it the point 'n click way:

Options -> Customize Emacs -> Top-level customization Group -> Convenience -> Follow -> Follow auto

---

### Post by Bluebottel on 2009-08-08
This will edit the submode but wont actually effect anything unless you invoke it.
I suggest you add the following to your ~/.emacs file to make it permanently start every time you start emacs.
```

(add-hook 'text-mode-hook
          '(lambda () (follow-mode)))

```

---

### Post by jpkotta on 2009-08-09
Nice tip.  BTW, I think you want to invoke follow-mode with a positive argument.  Running with no args just toggles.

```

(add-hook 'text-mode-hook
          '(lambda () (follow-mode 1)))

```

---

### Post by Bluebottel on 2009-08-17
> **jpkotta said:**
> Nice tip.  BTW, I think you want to invoke follow-mode with a positive argument.  Running with no args just toggles.

```

(add-hook 'text-mode-hook
          '(lambda () (follow-mode 1)))

```

Nice. That explains some random behaviour, thanks.

---

