---
title: "Core2Duo Quad hangs on boot"
date: 2010-04-08
forum: General Help
---

### Post by richiethom on 2010-04-08
Hi

I have just installed Ubuntu 9.10 64-bit onto an Intel Core2Duo vPro quad core machine, using the Alternative Installer.

The installation went fine, and Grub works as expected (dual boot with Vista). However, when the system boots, it gets as far as the brown screen with a kind of white blob moving across the screen under the Ubuntu logo, and hangs. I have to power down the system to be able to use it again.

Just before it hangs, the screen flickers slightly. The same happens if booting from the Live CD.

The graphics card is an nVidia Quadra, and has two monitors plugged into it.

Can anyone provide some guidance on how to narrow down the cause of this problem?

Thanks in advance

Rich

---

### Post by richiethom on 2010-04-08
Found it - I was booting with two screens attached.

---

### Post by hangfire on 2010-04-08
When hung, does Ctrl-Alt-F1 (or F2, etc) bring up a text console login prompt? This will help sort out whether it is X or Linux that has crashed.

BTW it's either a *Core 2 Duo* or a *Core 2 Quad*, it can't be both.

---

