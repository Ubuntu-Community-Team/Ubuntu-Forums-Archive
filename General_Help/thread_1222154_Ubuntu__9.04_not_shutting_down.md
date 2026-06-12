---
title: "Ubuntu  9.04 not shutting down"
date: 2009-07-24
forum: General Help
---

### Post by refit on 2009-07-24
When I exit Ubuntu 9.04 I get a message [71.027052] system halted and a blinking promt

---

### Post by LepeKaname on 2009-07-24
After > "system halted" what else your system is reporting?

---

### Post by wojox on 2009-07-24
Is this an old computer?

Add the option acpi=force to the end of your kernel line in /boot/grub/menu.lst

---

### Post by Tteddo on 2009-07-26
I just had a similar problem where the computer would not reboot or shutdown. Putting "acpi=force" the end of my kernel line did not work. After doing a lot of searching I found that putting "reboot=b" (without the quotes) there made it work perfectly. Apparently it has something to do with telling the bios to handle/control reboot/shutdown instead of the OS.

---

