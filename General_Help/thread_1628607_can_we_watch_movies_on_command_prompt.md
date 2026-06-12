---
title: "can we watch movies on command prompt"
date: 2010-11-22
forum: General Help
---

### Post by c2tarun on 2010-11-22
hi friends
this is kind of a silly question, but i just wanted to know.
what if i just install the kernel and no desktop or X win environment.
just use the linux purely from command prompt.
what kind of graphics facilities can a command prompt provide to us.
like can we watch movies??

---

### Post by t4thfavor on 2010-11-22
Im pretty sure theres an ascii movie player for the terminal, but most of them have so many gui deps that you will probably end up needing at very least an xserver.

---

### Post by fbnaia on 2010-11-22
You can use mplayer using the Framebuffer device as output...

mplayer -vo fbdev <filename>

---

### Post by lykwydchykyn on 2010-11-22
As long as your card has good framebuffer support, you can do quite a bit in a console.

take a look at _**[this]("http://kmandla.wordpress.com/2010/04/16/a-quick-look-at-framebuffer-applications/http://kmandla.wordpress.com/2010/04/16/a-quick-look-at-framebuffer-applications/")**_

---

### Post by Toz on 2010-11-22
ascii movies? (not for the faint of heart)

[http://everydaylht.com/howtos/eyecandy/ascii-movies/]("http://everydaylht.com/howtos/eyecandy/ascii-movies/")

Google "ascii movies" for many more links.

---

