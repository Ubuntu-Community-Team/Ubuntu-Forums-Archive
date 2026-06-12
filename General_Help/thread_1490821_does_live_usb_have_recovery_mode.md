---
title: "does live usb have recovery mode?"
date: 2010-05-22
forum: General Help
---

### Post by fffact on 2010-05-22
hi all.
i run 9.10 from a live usb with persistece, and got /etc/sudoers awfully messed up. now i'm told to fix in through 'recovery mode', but i don't think live usb has one. is that true? what about my sudoers? is there another way to fix it?

thanks

---

### Post by dcstar on 2010-05-22
> **fffact said:**
> hi all.
i run 9.10 from a live usb with persistece, and got /etc/sudoers awfully messed up. now i'm told to fix in through 'recovery mode', but i don't think live usb has one. is that true? what about my sudoers? is there another way to fix it?

thanks

In theory you can mount the CASPER-RW partition/file on another system and directly edit the files inside it, but I find it easier to just delete that totally if it gets screwed up too much.

---

### Post by jamesisin on 2010-05-22
You may want to repost this problem with a title such as "etc/sudoers says fix with 'recovery mode' ??".  Probably get better attention by those who can help.

---

### Post by fffact on 2010-05-23
> **dcstar said:**
> In theory you can mount the CASPER-RW partition/file on another system and directly edit the files inside it

yeah, i think i can do that. i think i can find a pristine /etc/sudoers too. and permissions should be 0440 right? but what about ownership? i mean, who should own /etc/sudoers?

thanks

---

