---
title: "Two Bootloaders after Wubi"
date: 2010-01-31
forum: General Help
---

### Post by baksa on 2010-01-31
Hi!

I have installed Ubuntu 9.10 with Wubi and uninstalled it. 
But now i have two bootloaders: GRUB and the XP bootloader with an Ubuntu option that doesn't work. 

How do I remove the XP bootloader?

---

### Post by oldfred on 2010-01-31
I think you have to edit boot.ini. I would make a backup and remove the wubi line. Do not use most linux editors as the line endings are different. You can use nano as I understand or any windows editor.

---

### Post by baksa on 2010-02-07
It worked like a charm! Thank you very much :D

---

