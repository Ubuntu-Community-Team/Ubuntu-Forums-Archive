---
title: "Set Virtual terminal to 80x25 [Ubuntu 9.10 Grub2]"
date: 2010-01-08
forum: General Help
---

### Post by skys on 2010-01-08
Simple question I think, but I've tried every tutorial I can find with no luck so far. I'm trying to set my virtual terminals to 80x25. Seemed simple enough in older versions of ubuntu. And I've made some progress, the initial startup is 80x25 for a brief moment before switching to a higher resolution. Tried setting all sorts of vga modes in hex values, played with fbset (Always gives me IOCTL error), editing header_.00 ..

So, I imagine this can't be as complicated as I'm making it out to be. Anyone else experience this, or knows how to resolve it?

(And to anyone wondering why I want such a low resolution? Full screen nethack though ssh ;) )

---

### Post by pbrane on 2010-01-08
maybe this will help:
[http://www.mjmwired.net/kernel/Documentation/svga.txt]("http://www.mjmwired.net/kernel/Documentation/svga.txt")

But I have tried to set my VT resolution to something other than 640x480 in grub2 with no luck. I have to use the vga=xxx kernel parameter.

---

### Post by skys on 2010-01-08
I've gone as far as this document I believe. However, using hex video modes just brings up an error message about them being 'depreciated'. Using 'ask' causes a'kernel must be loaded first' error. Although, I eventually did get this to work, once gnome starts to load, the resolution of all the virtual terminals switches to 1024x768 or so. So, I suppose, its something happening after the boot loader thats changing the terminal resolution, thats what I would like to know about.

---

