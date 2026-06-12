---
title: "Sudden blank screen after grub menu"
date: 2011-03-02
forum: General Help
---

### Post by gtim on 2011-03-02
I just rebooted an Ubuntu Server 10.04. After  choosing boot options in  the grub menu, though, it just displays a black  screen with the  blinking white underscore in the upper-left corner

 The machine has had (hardware) trouble with networking before, but  the  problem remains after 10 minutes, so I don't think it's the problem   now. Booting into recovery mode or using earlier kernels yields the same   problem. This also happens if I boot from another hard-drive. I cannot  access the virtual terminals (ctrl+alt+Fn) from the hung screen.

I haven't booted from CD as the machine lacks a CD reader. How should I diagnose the problem?

My boot options are:

```

recordfail
insmod ext2[FONT=monospace]
[/FONT]set root='(hd0,1)'[FONT=monospace]
[/FONT]search --no-floppy --fs-uuid --set 567[redacted][FONT=monospace]
[/FONT]linux /boot/vmlinuz-2.6.32-29-generic root=UUID=567[redacted] ro quiet splash[FONT=monospace]
[/FONT]initrd /boot/initrd.img-2.6.32-29-generic

```Removing quiet and splash doesn't chagne anything.

---

