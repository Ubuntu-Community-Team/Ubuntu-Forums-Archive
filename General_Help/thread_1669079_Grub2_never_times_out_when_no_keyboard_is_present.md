---
title: "Grub2 never times out when no keyboard is present"
date: 2011-01-17
forum: General Help
---

### Post by pingtoft on 2011-01-17
I just installed ububtu10.10 server on a fit-pc to use as a headless server.
If I don't attach a keyboard GRUB2 will wait indefinitely for a keystroke which kinda defeats the purpose of a headless server.
when I comment out 
GRUB_HIDDEN_TIMEOUT=0 
GRUB_HIDDEN_TIMEOUT_QUIET=true
it boots once, but next time the pc is coldbooted the problem is back.

I also tried adding 'acpi=off' and setting the timeout values to >0 but that doesn't seem to make a difference.

What to do?

---

### Post by ajgreeny on 2011-01-17
Can we see the whole of that **/etc/default/grub** file please; it might give more clues.

---

### Post by lithopsian on 2011-01-17
I haven't done this with GRUB 2 but certainly with GRUB legacy it works just fine.  Grub 2 should do the same.  Presumably you can see a screen.  Does it just sit on the boot menu forever even though you specify a timeout?

---

### Post by pingtoft on 2011-01-17
I don't have problems with GRUB legacy either.
It does indeed sit on the boot menu forever and if I attach a keyboard I can get it to boot.
I'll post the grub file later - I don't have a k/b atm.

Btw, I ran update-grub after modifying the grub file.

---

### Post by brycenesbitt on 2011-06-15
Same problem described here:
[http://serverfault.com/questions/243343/headless-ubuntu-server-machine-sometimes-stuck-at-grub-menu](http://serverfault.com/questions/243343/headless-ubuntu-server-machine-sometimes-stuck-at-grub-menu)

---

