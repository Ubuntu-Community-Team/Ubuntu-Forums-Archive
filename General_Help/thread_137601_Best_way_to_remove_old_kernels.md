---
title: "Best way to remove old kernels?"
date: 2006-02-28
forum: General Help
---

### Post by adie273 on 2006-02-28
Anyone know the best way to remove old unwanted kernels?

I only want 2 kernels maximum, the latest one i have and the one previous (Incase something goes wrong at some point). I don't really want kernels piling up and I think i have like 3 or 4 of them now. Not a big problem of course, but still.

Any help would be great

Adie

---

### Post by Irony on 2006-02-28
Just go to synaptic and uninstall them.

---

### Post by liger13 on 2006-02-28
whats a kernal?

---

### Post by adie273 on 2006-02-28
[QUOTE=liger13]whats a kernal?[/QUOTE]

Its the 'Core' of any operating system. Its the piece of software responsible for access to hardware and stuff.

Thanks Irony for the feedback, worked fine for me, not sure why, but i felt i tried that before and it didnt' work.

Oh well, works now so i dont care :)

---

### Post by az on 2006-02-28
[QUOTE=liger13]whats a kernal?[/QUOTE]
It's also just another package that you can add or remove....  That's the magic of apt, the backbone of the debian packaging system.

---

### Post by liger13 on 2006-02-28
is it the long list of names on the start up boot manager?

---

### Post by aalit on 2008-03-19
I really think that if you're replying to a post titled "Best way to remove old kernels?" you might as well be a little more explicit than just say "Go to Synaptic and uninstall it there". Seriously, I have no idea HOW to do it in Synaptic.

In other words, I'm a complete dummy ubuntu-wise. My intuition tells me removing kernels would have to do with Synaptic. But I need the step-by-step procedure. Thx

---

### Post by kpkeerthi on 2008-03-19
[IMG]http://www.howtogeek.com/wp-content/uploads/2007/09/image55.png[/IMG]

As you see from the GRUB screenshot, if you would like to remove the last two kernels (2.6.20-15 and 2.6.20-16) and keep the first one 2.6.22-10, boot into ubuntu desktop

1. System -> Admin -> Synaptic
2. Click **Search** on tool bar
3. Search for **linux-image-2.6.20-15**, right-click and choose Mark for Complete Removal
4. Now search for **linux-image-2.6.20-16**, right-click and choose Mark for Complete Removal
5. Click **Apply** on tool bar

After the kernel images are removed, ubuntu also removes corresponding entries from GRUB menu.
Hope it is clear.

---

### Post by Captainm on 2008-03-19
Beaten to it. How do I delete a post around here?

---

