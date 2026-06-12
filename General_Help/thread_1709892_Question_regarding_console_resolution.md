---
title: "Question regarding console resolution"
date: 2011-03-19
forum: General Help
---

### Post by jefelex on 2011-03-19
I've searched through this site and elsewhere to no avail :-(

Regular desktop computer with 10.04 64bit, runs great, no problem with the os at all, I've been using Ubuntu since 7.04

My question is:  If I choose to boot in console mode, editing grub2 (properly with /etc/grub.d) and have my OS boot into console mode, how do I adjust the resolution of the final console screen once grub has finished and upstart has concluded?

I run gnome from the console with `sudo gdm' after I have logged in to the console. (runs just as well and as fast as if I have it boot into gnome normally) The resolution of gnome is 1024x768 @ 75hz, but I find that at that resolution on the console screen, I can't read the screen very well (eyes are gettin old I guess!) 

How can I adjust the console resolution - I can change grubs boot resolution easily with grub, its just that once the grub has finished, it changes to 1024. I've tryed  GRUB_GFXMODE  and the other option with that (Can't remember exactly what it is called right now) preload or something like that

I've looked through /etc/xinit and other obvious places, and can't seem to find this - it's a real stumper! I usually never come here asking questions, I like figuring it out myself, but I'm done!

Any ideas would surely be appreciated! :-)

John

---

