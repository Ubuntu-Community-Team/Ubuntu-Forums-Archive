---
title: "How I solved my wireless random freeze problem"
date: 2006-04-30
forum: General Help
---

### Post by blackmath on 2006-04-30
After I got the wireless card on my Dell D410 working via ndiswrapper, my machine would randomly and completely freeze a few minutes after I enabled wireless. This is my card from lspci:

```

0000:02:03.0 Network controller: Broadcom Corporation: Unknown device 4319 (rev 02)
```

I suspected it was an IRQ conflict and found this solution:

Add  pci=noacpi to the end of the menu item in /boot/grub/menu.lst:

```
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro quiet splash **pci=noacpi**
```

I can now use wireless and ethernet just fine. Everything works like a beauty.

---

### Post by n3tfury on 2006-04-30
out of curiosity, where did you find this?

---

### Post by blackmath on 2006-04-30
I'm sorry I didn't keep the URLs I visited and it took a while to find. It was a thread somewhere in association with a problem someone had with IRQ sharing for yenta PCMCIA cards, I just tried it and it solved my problem too. It would be nice to know why it works.

---

### Post by n3tfury on 2006-04-30
Indeed.  glad you're up and running though!

---

