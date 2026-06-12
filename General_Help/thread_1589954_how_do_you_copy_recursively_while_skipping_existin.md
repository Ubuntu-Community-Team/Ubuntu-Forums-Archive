---
title: "how do you copy recursively while skipping existing files?"
date: 2010-10-07
forum: General Help
---

### Post by ravi84m on 2010-10-07
I'm trying to copy some files via terminal because i had some issues with nautilus crashing in the middle of the operation.
So how can i copy files recursively while skipping existing ones?
thanks in advance.

---

### Post by luvshines on 2010-10-07
> **ravi84m said:**
> I'm trying to copy some files via terminal because i had some issues with nautilus crashing in the middle of the operation.
So how can i copy files recursively [COLOR="Blue"]while skipping existing ones[/COLOR]?
thanks in advance.

Couldn't understand this

---

### Post by marcisim on 2010-10-07
Have files you want to copy the same xtension and the other a different one?

---

### Post by ravi84m on 2010-10-07
> **luvshines said:**
> Couldn't understand this
copy a folder that contains other files to another folder with some of the files already copied.

> **marcisim said:**
> Have files you want to copy the same xtension and the other a different one?
yes... i basically copied the same folder but natilus crashed.

---

### Post by HermanAB on 2010-10-07
Howdy,

You can use rsync as a better kind of copy.

---

### Post by irishbreakfast on 2010-10-07
or 'cp -r -n' should do it. 
Please 'man cp' first to make sure it is what you want.

---

### Post by ravi84m on 2010-10-07
> **HermanAB said:**
> Howdy,

You can use rsync as a better kind of copy.

i tried ```
sudo rsync -r /from /to
```
but i get the error ```
rsync error: received SIGINT, SIGTERM, or SIGHUP (code 20) at rsync.c(543) [sender=3.0.7]
```
any suggestions?

---

### Post by ravi84m on 2010-10-07
> **irishbreakfast said:**
> or 'cp -r -n' should do it. 
Please 'man cp' first to make sure it is what you want.
Thanks. exactly what i was looking for...

---

