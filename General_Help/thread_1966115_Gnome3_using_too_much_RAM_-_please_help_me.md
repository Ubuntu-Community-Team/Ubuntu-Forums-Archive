---
title: "Gnome3 using too much RAM - please help me"
date: 2012-04-26
forum: General Help
---

### Post by CProgramming on 2012-04-26
Hello! I've just installed ubuntu 12.04 with gnome3 interface.

I'm using 32bit OS and I have 4GB RAM.

I tried to "free -m" on terminal and thats the results:

```
[COLOR=#000000][COLOR=#0000BB]nimrod[/COLOR][COLOR=#007700]@[/COLOR][COLOR=#0000BB]nimrod[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]Product[/COLOR][COLOR=#007700]:~$ [/COLOR][COLOR=#0000BB]free [/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]m
             total       used       free     shared    buffers     cached
Mem[/COLOR][COLOR=#007700]:          [/COLOR][COLOR=#0000BB]3767       3379        387          0        228       2538
[/COLOR][COLOR=#007700]-/+ [/COLOR][COLOR=#0000BB]buffers[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]cache[/COLOR][COLOR=#007700]:        [/COLOR][COLOR=#0000BB]612       3154
Swap[/COLOR][COLOR=#007700]:         [/COLOR][COLOR=#0000BB]3963          1       3962
nimrod[/COLOR][COLOR=#007700]@[/COLOR][COLOR=#0000BB]nimrod[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]Product[/COLOR][COLOR=#007700]:~$  [/COLOR][/COLOR]
```

That's when I using only firefox!

[IMG]http://img31.imageshack.us/img31/449/13354795338426.png[/IMG]

Why does gnome3 \ Ubuntu using so much RAM?  And how can I fix it?

Thanks! :)

---

### Post by cryptotheslow on 2012-04-26
It's not. The important figure is on the -/+ buffers/cache line. Highlighted in red below.

```

nimrod@nimrod-Product:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3767       3379        387          0        228       2538
-/+ buffers/cache:        612       [COLOR=Red]**3154**[/COLOR]
Swap:         3963          1       3962
nimrod@nimrod-Product:~$

```

The cache is available for use if required.

There's a good explanation here:
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

