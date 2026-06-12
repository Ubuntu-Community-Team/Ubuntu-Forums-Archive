---
title: "grub2 temporary default"
date: 2011-06-23
forum: General Help
---

### Post by sj1410 on 2011-06-23
Hi,

is it possible in grub2, that a temporary default entry. For example

i have 2 menuentry in grub.cfg 0 & 1. my default is 0 but i want to automatically boot once to 1 and it changes back to 0.

I hope i am clear on my requirement.


Please suggest.

---

### Post by iclestu on 2011-06-23
> **sj1410 said:**
> Hi,

is it possible in grub2, that a temporary default entry. For example

i have 2 menuentry in grub.cfg 0 & 1. my default is 0 but i want to automatically boot once to 1 and it changes back to 0.

I hope i am clear on my requirement.


Please suggest.

If I understand your question correctly it seems like a lot of hassle to automate it for just one boot? Cant you just boot manually into the other os once? Surely thats easier than changing grub default twice!?

---

### Post by sj1410 on 2011-06-23
Thats ok, but looking for something to automize it.

---

### Post by Dave_L on 2011-06-23
See: [grub-reboot]("http://manpages.ubuntu.com/manpages/lucid/en/man8/grub-reboot.8.html")

---

### Post by sj1410 on 2011-06-23
Wow!! Wow!! Wow!! 

You are great Dave. This is what i was looking for. Thanks a lot.

---

