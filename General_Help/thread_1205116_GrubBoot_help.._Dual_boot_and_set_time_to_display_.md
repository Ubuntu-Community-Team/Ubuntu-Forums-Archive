---
title: "Grub/Boot help.. Dual boot and set time to display at 0.."
date: 2009-07-05
forum: General Help
---

### Post by iamdavid on 2009-07-05
I can't seem to find a way to fix what seems to be a simple problem. I've had a dual boot Ubuntu/Vista setup for a couple years now for work. Windows is set to be the default OS. I recently changed the time I have to select an OS all the way to 0. Now I can't boot into Ubuntu at all. Holding down any key doesn't work, it just flies by the Grub boot loader..

Any suggestions would be greatly appreciated..

---

### Post by michy99 on 2009-07-05
If you can boot from a Live CD, mount the partition with Ubuntu and edit /boot/grub/menu.lst and change the line that says timeout.

---

### Post by iamdavid on 2009-07-05
> **michy99 said:**
> If you can boot from a Live CD, mount the partition with Ubuntu and edit /boot/grub/menu.lst and change the line that says timeout.

Thanks for the quick repy! I'm able to boot to the live cd and open the file but can't save it.. Can you tell me what to do next?

---

### Post by merlinus on 2009-07-05
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by iamdavid on 2009-07-05
> **merlinus said:**
> ```
gksudo gedit /boot/grub/menu.lst
```

You're awesome! Thanks a million.

---

### Post by merlinus on 2009-07-05
Glad it worked.  In general you need to use sudo (or gksudo for graphical apps) as a prefix in commands for editing files and such that are owned by root.

---

