---
title: "High consume of memory"
date: 2006-05-02
forum: General Help
---

### Post by mjs on 2006-05-02
Hi,

I'm using the gnome in the kubutu because I can't yet fix my problem with KDE.

The consume of memory is very high, yesterday using the apps:

- Kate
- Nautilus ( 2x )
- Gnome-terminal

The xorg uses about 55% of memory ram, my swap was used 100%.

Why?

Thanks

---

### Post by byenary on 2006-05-02
try
the command top
in the terminal to look whats going on

---

### Post by barbarian on 2006-05-02
Hei, to display top memory user:
 $ ps aux | sort -n +3 | tail -1

also check this out:
[http://www.rampant-books.com/t_linux_9_ps_memory_aux.htm](http://www.rampant-books.com/t_linux_9_ps_memory_aux.htm)

---

### Post by Al3xanR0 on 2006-05-02
[QUOTE=barbarian]Hei, to display top memory user:
 $ ps aux | sort -n +3 | tail -1

also check this out:
[http://www.rampant-books.com/t_linux_9_ps_memory_aux.htm](http://www.rampant-books.com/t_linux_9_ps_memory_aux.htm)[/QUOTE]

Cool this rocks!! Thanks;)

---

