---
title: "can I turn off usplash?"
date: 2006-06-26
forum: General Help
---

### Post by Hiroshima on 2006-06-26
I read one possible solution to the "will now halt" bug was to turn off usplash when shutting down the system (sorry, can't find the link now).  Usplash is pretty, but I'm willing to turn it off if it'll help me power down now.

I don't know if it's related, but PCMCIA says "failed" at startup.

Thanks for any ideas,

Hiroshima

---

### Post by tonyr on 2006-06-26
Edit **/boot/grub/menu.lst** ( you must do it as **root**).  Find all lines
starting with **kernel**, and remove the word **splash** from the line,
assuming, of course, that it is there.

---

### Post by mlind on 2006-06-26
Better way would be using defoptions line on /boot/grub/menu.lst.
Otherwise your changes are lost next time update-grub is invoked.

```

# defoptions=**nosplash**

```

and then run *sudo update-grub*

---

