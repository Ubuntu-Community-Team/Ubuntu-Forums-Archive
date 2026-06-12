---
title: "kernel troubles"
date: 2010-02-07
forum: General Help
---

### Post by CO_Shifty on 2010-02-07
Hello Everyone, so I noticed that my karmic install (upgraded from Jaunty) booted from kernel 2.6.27-16, even though it had updated to 2.6.27-19.

I decided to uninstall 2.6.27-16 and all old versions, now the entry in grub disappeared, so I now can't boot.

I found out about chroot in LiveCd and installed linux-image, which to my surprised installed 2.6.31-19. Then I installed grub-pc and it said it successfully detected the image, plus my Windows install.

Unfortunately, it didn't make a difference, old grub still boots with no ubuntu entry.

I wonder how can I fix this?

*EDIT: I got it to boot by adding an entry to list file in /boot/grub. And I'm not sure I ever had 2.6.27-16 installed since residual configs suggest otherwise.

I still don't know why I don't have grub 2 booting though.

---

