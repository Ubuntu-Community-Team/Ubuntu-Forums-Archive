---
title: "Need help with Conky"
date: 2011-11-28
forum: General Help
---

### Post by M!SF!TS on 2011-11-28
I was wondering if someone could tell me this issue with this conky?

conky_orange: [http://gnome-look.org/content/show.php/conky_orange?content=137503&PHPSESSID=10e2bedd140347bde439af5fc42f95bc](http://gnome-look.org/content/show.php/conky_orange?content=137503&PHPSESSID=10e2bedd140347bde439af5fc42f95bc)

I installed it just like the directions said.
(create a .conky file in the home directory, and copied conkyrc_orange and conky_orange.lua into it)

then I typed this in my terminal:
```
conky -c ~/.conky/conkyrc_orange
```

I get this as my output:
```
me@Ubuntu:~$ conky -c ~/.conky/conkyrc_orange
Conky: forked to background, pid is 3929
me@Ubuntu:~$ 
Conky: desktop window (1000023) is subwindow of root window (159)
Conky: window type - override
Conky: drawing to created window (0x1400001)
Conky: drawing to double buffer

```

conky **is** a running process: 
```
ps -u me
```
```
.
.
.
.
.
.
.3982 ?        00:00:00 nautilus
 4001 ?        00:00:01 chromium-browse
 4014 pts/0    00:00:00 conky
 4023 pts/0    00:00:00 ps
me@Ubuntu:~$ 

```

but my screen looks like this:

[IMG]http://i606.photobucket.com/albums/tt143/JacksonNicholasJ/Screenshot1.png[/IMG]
no conky
help me :(

---

### Post by M!SF!TS on 2011-11-29
> **scratch178 said:**
> i just took a quick look on your conky.

i had the same problem when i updated to 11.10

replace 
window type - override
with
own_window_type desktop

and then go to 
advanced settings --> desktop --> Have file manager handle the desktop --> OFF

this should do the trick,


Here: [http://ubuntuforums.org/showthread.php?t=281865&page=1894](http://ubuntuforums.org/showthread.php?t=281865&page=1894)

---

