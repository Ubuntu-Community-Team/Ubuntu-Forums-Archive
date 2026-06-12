---
title: "How can I find the right driver for ubuntu"
date: 2012-04-10
forum: General Help
---

### Post by mjsilverstri on 2012-04-10
hi,

I have a new Dell Latitude laptop, I would like to know if there is a right driver for my graphic card on my laptop?

Right now,I get ubuntu 11.10 to boot up, but when I run Gnome 3 shell, I only get the 'classic gnoome' environment.

Thank you.

---

### Post by cortman on 2012-04-10
Are you certain you're selecting Gnome 3 and not Gnome fallback? It's the little gear icon next to where you type your password.
If so, open a terminal and copy/paste in the following:

```
lspci | grep -i vga
```

and

```
lshw -C video
```

Please post output here.

---

