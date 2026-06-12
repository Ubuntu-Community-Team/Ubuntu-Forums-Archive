---
title: "Text color tty1-tty6"
date: 2009-07-22
forum: General Help
---

### Post by my.self on 2009-07-22
Hi!

Just a short question...

How can i change the text color of a Terminal (tty1-tty6) ?

Changing the colors in the Gnome Terminal wasn't a big issue...
Some of the colors were also applyed to Terminals tty1-tty6
but the typed text in is still white ;-(


cheers Stefan

---

### Post by SuperSonic4 on 2009-07-22
Add something similar to the following to your .bashrc file (you can edit this as user)
[\t] is time. The last one (after the $) is the colour, you can change this to something else and it should change the colour. I changed the 01 part to 01 and it gave me a greenish colour

```
PS1='[\t] \[\e[0;35m\]\u \[\e[1;34m\]\w \[\e[1;32m\]\$ \[\e[3;01m\] '
```

Note that will only work for your user, if anyone else wants to use it they need to edit their bashrc and I don't believe root has a bashrc

---

### Post by my.self on 2009-07-25
thx!

---

