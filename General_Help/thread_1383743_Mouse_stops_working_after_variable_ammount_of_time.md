---
title: "Mouse stops working after variable ammount of time"
date: 2010-01-17
forum: General Help
---

### Post by Prestidigitator on 2010-01-17
I running 9.10 on a Dell Dimension E521. I have a Logitech V100 notebook mouse. For some reason the mouse stops working after I've used it for a while. If I move it slowly it will last longer than if I wave it across the screen as fast as I can. I found some other threads by people who were having the same problem, but nothing I found fixed the problem. One person said that I needed to add acpi=force irqpoll to /boot/grub/menu.lst, but I couldn't find it when went to /boot/grub or when I searched for it. Some people said I needed to restart the x server or udev, but that didn't work either.

---

### Post by tom4everitt on 2010-01-17
In ubuntu 9.10 the /boot/grub/menu.lst is replaced by /boot/grub/grub.cfg. 

This file your not supposed to edit directly though. Try make the same change to /etc/grub.d/10_linux

and then run sudo update-grub

---

### Post by Prestidigitator on 2010-01-17
They said to put "acpi=force irqpoll" after "defoptions=", and I couldn't find that, so I guess that's not going to work.

---

### Post by Prestidigitator on 2010-01-17
It turns out it's a problem with my computer. I need to buy a pci usb hub.

---

