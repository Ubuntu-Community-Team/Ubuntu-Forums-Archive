---
title: "framebuffer without grub2"
date: 2011-06-08
forum: General Help
---

### Post by frank_n on 2011-06-08
My ubuntu 11.04 boots from Windows using grub4dos. That's
to say no grub2 and that is not going to be changed.

(1) If 'nomodeset' is given as kernel option, KSE gives me a
framebuffer which I cannot control - neither with 'fbset'
nor with 'fbcon'. Is there a way?

(2) Avoiding 'nomodeset' as kernel option gives me no
framebuffer at all. Is there a way to get it with some other
kernel option? vga=xxx does not work, video:yyy does not work.

(3) Is there a way to activate the framebuffer after
booting? fbset and fbcon only act on existing e.g. /dev/fb0.

I have been googling the problem for about two weeks and
there are tons of related posts and queries. Nonetheless my
results are essentially negative: (i) links older than one
year are useless; (ii) links to discussions on distros other
than ubuntu are useless.

Somebody knows better?


Thanks!

frank

---

