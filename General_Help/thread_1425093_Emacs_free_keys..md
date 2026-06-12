---
title: "Emacs free keys."
date: 2010-03-08
forum: General Help
---

### Post by bkasterm on 2010-03-08
I have some emacs packages interact with eachother, to solve this I am looking to rebind a function.  I however cannot find a reasonable key combination to use (anything that comes to mind is already mapped somewhere).  Is there a standard to use for newly defined commands?  How can I find out which say length two combinations are not used?

thanks.

Best,
Bart

---

### Post by rafita on 2010-03-08
You can type C-h k (describe-key) to check if some key binding you want to
use is free. But I think that C-c "letter" are reserved to be defined by the user.

---

### Post by jpkotta on 2010-03-09
From the manual:
> 
57.4.1 Keymaps
--------------

...

   As a user, you can redefine any key, but it is usually best to stick
to key sequences that consist of `C-c' followed by a letter (upper or
lower case).  These keys are "reserved for users," so they won't
conflict with any properly designed Emacs extension.  The function keys
<F5> through <F9> are also reserved for users.  If you redefine some
other key, your definition may be overridden by certain extensions or
major modes which redefine the same key.


Also, C-c C-<key> bindings are conventionally reserved for major modes.

Typing C-h b will show all the bindings in the current buffer (keybindings are buffer local in general because a local-set-key will override a global-set-key).

---

### Post by bkasterm on 2010-03-11
Thanks for the help.  I found that indeed the C-c<letter> keys are available other than the ones set in my .emacs .

---

