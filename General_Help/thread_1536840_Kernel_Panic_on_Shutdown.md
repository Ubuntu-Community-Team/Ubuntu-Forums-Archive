---
title: "Kernel Panic on Shutdown"
date: 2010-07-22
forum: General Help
---

### Post by mpn_1990 on 2010-07-22
Everytime I try to shutdown or restart, a kernel panic occurs with the caps and scroll lock lights blinking. Nothing is displayed on the screen, and dmesg doesn't seem to show anything panic related. How can I start to diagnose this? Everything else runs pretty well, on Lubuntu 10.04.

---

### Post by mpn_1990 on 2010-07-22
Edit: It reboots from one of the VT's perfectly fine "sudo reboot".

"sudo shutdown now" will get it to hang at the lubuntu logo but not flash the keyboard lights. Tapping numlock still works, but it doesn't shut off. 

"sudo poweroff" works perfectly as well, from the VT's.

Any attempt to shutdown or reboot from X or an X application panics.

---

### Post by cavalier911 on 2010-07-23
Hold **shift** key down if the Grub2 menu is hidden until it appears.

When grub2 menu appears hit the**  e **key.

Remove quiet splash from kernel line so  you can see errors .

Start experimenting by booting with the kernel options here:

[https://help.ubuntu.com/community/BootOptions#Common%20Boot%20Options](https://help.ubuntu.com/community/BootOptions#Common%20Boot%20Options)

**Ctrl+x** to boot.

When you find the options that work follow the directions for adding to grub2 permanently.

Investigate motherboard bios options you can change which may stop the panic.

Good luck !

---

