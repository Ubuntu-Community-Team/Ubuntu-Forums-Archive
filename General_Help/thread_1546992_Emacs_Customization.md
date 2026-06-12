---
title: "Emacs Customization"
date: 2010-08-06
forum: General Help
---

### Post by groonrix on 2010-08-06
Hello.
I've been trying to modify my emacs settings by installing this elisp file:
[http://wiki.cs.huji.ac.il/wikis/MediaWiki/cs/images/cs/images/b/b6/Elisp.tar.gz](http://wiki.cs.huji.ac.il/wikis/MediaWiki/cs/images/cs/images/b/b6/Elisp.tar.gz)
and linking its content to /usr/local/share/emacs/site-lisp/site-start.el,
and other various locations found with the following command:[FONT=monospace]
[/FONT]```
emacs --no-init-file --no-site-file --batch --eval "(princ load-path)" | tr ' ' '\n'
```
But I can't get it work. I must be missing something.
Thanks in advance.

---

### Post by dandnsmith on 2010-08-06
Did you install the other 'may be needed' stuff mentioned at that site?

---

### Post by groonrix on 2010-08-06
[LEFT]No.
The site ([http://wiki.cs.huji.ac.il/wiki/Emacs](http://wiki.cs.huji.ac.il/wiki/Emacs)) also mentions gnus and AUCTeX packages, but as far as I understood these are not required when installing the customization.
Thanks!
[/LEFT]

---

