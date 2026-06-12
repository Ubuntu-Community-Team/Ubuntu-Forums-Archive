---
title: "Looking for Decent Grub Editor"
date: 2010-03-14
forum: General Help
---

### Post by Topher88 on 2010-03-14
My grub menu is getting sort of out of hand...  It seems like it's saved every single kernel update, so there are like five or six there, so including the updates and the recovery versions, that's like ten entries right there!  I need something that will allow me to shorten the amount of kernels that show up, and I'd also like to edit the order in which they appear.

I installed Startup-Manager, but it's pretty worthless...  Doesn't do anything that I need it to.  I've seen screencaps that show that it *has* better features, but I'm not seeing them.  Why?  All I can really do with it is change the resolution and a few other useless things.

I used to have Ubuntu Studio, and I had a really good one, but I can't remember what it was called for the life of me...  It did everything I needed it to - including shortening the list, in this case.  I want to say it was KDE something or other, but it wasn't kgrubeditor...  

Anyway...  I either need to know why Startup-Manager isn't doing what I want it to do, or to be lead in the direction of a program that can.

Thanks!

---

### Post by linuxman94 on 2010-03-14
> **Topher88 said:**
> I need something that will allow me to shorten the amount of kernels that show up,


You can uninstall old kernels in synaptic.  Search for linux-image and remove some of the older ones.  I recommend you leave at least one older kernel in case the new one decides not to boot ;)

---

### Post by dcstar on 2010-03-14
> **Topher88 said:**
> 
........
Anyway...  I either need to know why Startup-Manager isn't doing what I want it to do, or to be lead in the direction of a program that can.


Startup-Manager seems to work ok with grub-legacy, but Grub2 is another matter.

---

### Post by Topher88 on 2010-03-14
> **dcstar said:**
> Startup-Manager seems to work ok with grub-legacy, but Grub2 is another matter.

I had a feeling that might have something to do with it...

---

### Post by Bradj47 on 2010-03-14
> **Topher88 said:**
> My grub menu is getting sort of out of hand...  It seems like it's saved every single kernel update, so there are like five or six there, so including the updates and the recovery versions, that's like ten entries right there!  I need something that will allow me to shorten the amount of kernels that show up, and I'd also like to edit the order in which they appear.

I installed Startup-Manager, but it's pretty worthless...  Doesn't do anything that I need it to.  I've seen screencaps that show that it *has* better features, but I'm not seeing them.  Why?  All I can really do with it is change the resolution and a few other useless things.

I used to have Ubuntu Studio, and I had a really good one, but I can't remember what it was called for the life of me...  It did everything I needed it to - including shortening the list, in this case.  I want to say it was KDE something or other, but it wasn't kgrubeditor...  

Anyway...  I either need to know why Startup-Manager isn't doing what I want it to do, or to be lead in the direction of a program that can.

Thanks!

Try doing it the old fashioned way: By using a text editor. I find that way easier than looking for a GRUB editor that actually works, installing it, and figuring out how it works. Just editing the menu with gedit is easy. You just delete the entries you don't want.

---

### Post by colobix on 2010-03-14
If you have KDE4 or newer I recommend KGRub Editor.
[http://lazyubuntu.com/kgrubeditor-a-grub-editor-for-kde-4.html](http://lazyubuntu.com/kgrubeditor-a-grub-editor-for-kde-4.html)
Works like a charm.

---

