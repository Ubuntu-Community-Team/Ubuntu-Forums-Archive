---
title: "asking about a command line"
date: 2010-06-18
forum: General Help
---

### Post by htoofe on 2010-06-18
Hi Ubuntu Community..

I'm sure there is a command in the terminal which allow you..
to detect input signals from a mouse or joypad..
I saw it one time and I'm really having a hard time finding it..
all that I remember if you typed that command a window will appear and it will wait until you press a mouse button or scroll a volume wheel.. then it will show a text or numbers every time you scroll the volume wheel or press mouse button or move the mouse it will detect it..

any one have an Idea about that command??
Thanks in advance

---

### Post by gzarkadas on 2010-06-18
Maybe you mean `[mev]("http://linux.die.net/man/1/mev")' from the `gpm' package? Or `[xev]("http://linux.die.net/man/1/xev")' its equivalent for GUI environments?

---

### Post by i.r.id10t on 2010-06-18
tail -f /dev/psaux ?

---

