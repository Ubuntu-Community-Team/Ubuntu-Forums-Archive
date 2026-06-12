---
title: "GNU Emacs"
date: 2006-06-15
forum: General Help
---

### Post by wizzkid on 2006-06-15
Hi, Is there a way to turn on the line number on Emacs? I find this software good, however, I think that with line number is much better.

Thanks,

---

### Post by buttari on 2006-06-15
add 
```

(line-number-mode t)

```
to your .emacs file.

alfredo

---

### Post by wizzkid on 2006-06-15
where could I find that file? :)

I tried on  /usr/bin/emacs it says that the fileis binary, thus editing will corrup the file.  I also tried to seach on /home/user/.emacs/ theres no file in there, only 1 folder which is autosave

any help?

Thanks

---

### Post by oscar on 2006-06-15
create a .emacs file in your home directory

---

### Post by wizzkid on 2006-06-16
I already aded (line-number-mode t) on .emacs, but thre's still no line number on the left side. :-(  here's my .emacs
```

(custom-set-variables
  ;; custom-set-variables was added by Custom -- don't edit or cut/paste it!
  ;; Your init file should contain only one such instance.
 '(case-fold-search t)
 '(current-language-environment "UTF-8")
 '(default-input-method "rfc1345")
 '(global-font-lock-mode t nil (font-lock))
 '(show-paren-mode t nil (paren))
 '(transient-mark-mode t))
(custom-set-faces
  ;; custom-set-faces was added by Custom -- don't edit or cut/paste it!
  ;; Your init file should contain only one such instance.
 )
(line-number-mode t)

```

any suggestions? :)

---

### Post by fast1 on 2006-06-16
The line number appear just in the bar where there is also the name of the buffer.
It is set to true by default. So, I think you don't need to change the .emacs file.
I don't know if there's a way to show it also in the left side.

---

