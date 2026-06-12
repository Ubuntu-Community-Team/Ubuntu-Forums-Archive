---
title: "A question about emacs set-key"
date: 2011-05-09
forum: General Help
---

### Post by TheHimself on 2011-05-09
I'd like to define a key binding in emacs so that when I press F2, the current file is saved, then LaTexed and the result is previewed. Firstly, I don't know how to assign more than one command to a key.  

Secondly when I put the following in .emacs

(global-set-key   (kbd "<f2>")    'tex-file)

and press F2, I get the message "Symbol's function definition is void".

---

### Post by TheHimself on 2011-05-10
Any ideas anybody?

---

