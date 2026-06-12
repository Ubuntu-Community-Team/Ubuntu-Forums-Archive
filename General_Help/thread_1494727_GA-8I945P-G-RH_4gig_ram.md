---
title: "GA-8I945P-G-RH 4gig ram"
date: 2010-05-27
forum: General Help
---

### Post by thebigob on 2010-05-27
Hi all,

I have a gigabyte [COLOR=#FD6724][COLOR=Black]GA-8I945P-G-RH motherboard.

I have recently upgraded the ram to 4 gig which is what the manual says is the max it can take.

My problem is that when the system boots it only sees 3.4 gig and when I run 64 bit lucid it only see's 3.2 gig

Doing a uname -a i get x86_64 so its defo the 64 bit version I am running I just dont know why its not seeing 800mb of ram.

Does anyone else have this board or know how to fix this issue?

Im guessing there must be a configuration in the bios or something I am missing?

Any ideas gratefully received.
[/COLOR][/COLOR]

---

### Post by egalvan on 2010-05-27
When a computer boots, it uses RAM for various functions, 
such as data/code pages, pointers, tables, scratch-pads, copies of firmware, etc.
If the video is on-board, it also uses RAM.
These are portions that cannot be paged out, so they are not reported in the "usable" amount.

This is normal

Then when the OS itself boots, it needs some persistent storage, so this also lowers the "usable" RAM.

Again, this is normal

So your four gigabytes drops to 3.2, or 3.6, or whatever.

All normal.

---

### Post by thebigob on 2010-05-27
Thanks for your reply.

I have an external video card so guess I was just shocked that the drop was so considerable.

---

