---
title: "Un-brick?"
date: 2009-10-23
forum: General Help
---

### Post by Anonymousable on 2009-10-23
OK, I've installed grub2 on Ubuntu 9.10 which was *upgraded* from ubuntu 9.04.

I ran update-from-grub-legacy, not knowing that I needed to check if grub2 worked properly *first*.

So, in short, I've semi-bricked my computer, and am posting this while booting from a Live CD. How can I "undo" the update-from-grub-legacy?

Thanks in advance.

---

### Post by Anonymousable on 2009-10-23
Sorry to bump so soon (you may know this behavior from the topic where this problem originated), but I really need my computer back to normal...

Is there a way to undo update-from-grub-legacy from the LiveCD?

---

### Post by sanderj on 2009-10-23
Have you tried the standard procedure to restore grub?

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

---

### Post by Anonymousable on 2009-10-23
> **sanderj said:**
> Have you tried the standard procedure to restore grub?

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)
Thanks... But no.
```
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found

```

---

### Post by Anonymousable on 2009-10-23
Wait, SOLVED! All I had to do was grub-install /dev/sda5 and then the instructions you gave me worked! Thanks very much.

---

