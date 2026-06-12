---
title: "Emacs Comment Multiple lines"
date: 2011-09-18
forum: General Help
---

### Post by nachiappantce on 2011-09-18
Hi All,

I am using Emacs for C programming. To comment multiple lines I use C-c C-c. To uncomment multiple lines the tutorial says give negative argument and C-c C-c. How do i provide negative argument ?

Thanks and Regards
Nachi

---

### Post by jpkotta on 2011-09-25
You can provide a negative argument with M-- (Alt + dash), or C--, or C-M--.  You can see all of the keys this is bound to with C-h w negative-argument.  negative-argument is basically the same as universal-argument (C-u), so you can type numbers after it too.  Also, you can always give a numeric argument after C-u, including negative ones (e.g. C-u - 5 C-f will move backwards 5 characters).

What I do in this particular case is use comment-dwim, which is usually bound to M-;.  If you have transient-mark-mode on (the default in Emacs 23 and newer), and you select a region, it will detect comments and remove them, otherwise it will insert a comment.  C-c C-c is specific to cc-mode, but comment-dwim works with several major modes.

---

