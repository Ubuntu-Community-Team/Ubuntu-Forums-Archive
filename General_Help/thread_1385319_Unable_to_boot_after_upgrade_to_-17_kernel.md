---
title: "Unable to boot after upgrade to -17 kernel"
date: 2010-01-19
forum: General Help
---

### Post by lloyd_b on 2010-01-19
I upgraded to the latest kernel (2.6.31-17 IIRC), but now I'm unable to boot Xubuntu (via Wubi).  Whenever I select "Xubuntu" from the Wubi menu, instead of getting the Grub menu, I get a command prompt at ("sh:grub>") instead.

I still have the -16 kernel installed, so If I can figure out how to get it to boot, I can probably recover the rest myself.  But between my unfamiliarity with Grub, and the fact I have no clue what all parameters are needed to get Grub to boot a Wubi loopback, I'm kinda lost.

(Note: In the grub shell, when I specify "linux /boot/vmlinuz-2.6.31-17-generic", I get an error "Invalid magic number".  When I do the same for the -16, it appears to accept it.  So I'm guessing I have a corrupt kernel image)

Lloyd B.

---

### Post by lloyd_b on 2010-01-19
Okay, nevermind.  After some more searching, it turns out this is a known Wubi bug.

For anyone else with a similar problem, download and install [this patch for "wubildr"]("https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210").

Lloyd B.

---

