---
title: "ubuntu 10.10 will not shutdown"
date: 2011-01-16
forum: General Help
---

### Post by caleb856 on 2011-01-16
I installed ubuntu 10.10 32bit on my computer and it does not shutdown properly, it hangs on the desktop wallpaper. i also installed linux mint 32bit and it has the same problem. but when i installed ubuntu 10.10 64bit, it does not have that problem.

---

### Post by TheHackOps on 2011-01-16
If you go into console and type sudo reboot does it reboot?

---

### Post by karthick87 on 2011-01-16
In terminal type,

```
sudo poweroff
```

---

### Post by ronnielsen1 on 2011-01-16
Is this an older box? It might need acpi=off 

Try this when booting by adding it to the string at the end. If it works:

gksudo gedit /etc/default/grub

Find the following line and add acpi=off to the end
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

save and hit sudo update-grub

---

### Post by caleb856 on 2011-01-16
[SIZE=1]When i run "sudo poweroff" and "sudo reboot" it gives me this error message
[38.557040] phy0 - rt2800_wait_wmpda_ready: Error - wpdma TX/RX buys, abrrting.
[38.647090 ] phy0- rt2x00pci_regbusy_read:Error - indirect register access has failed: offset 0x00007010, value 0xffffffff

then it just freezes
[/SIZE]

---

### Post by caleb856 on 2011-01-16
> **ronnielsen1 said:**
> Is this an older box? It might need acpi=off 

Try this when booting by adding it to the string at the end. If it works:

gksudo gedit /etc/default/grub

Find the following line and add acpi=off to the end
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

save and hit sudo update-grub

I tried that and it still froze

---

