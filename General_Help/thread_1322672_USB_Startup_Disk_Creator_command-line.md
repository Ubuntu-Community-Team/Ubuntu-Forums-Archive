---
title: "USB Startup Disk Creator command-line"
date: 2009-11-11
forum: General Help
---

### Post by Calixte on 2009-11-11
I have a problem with creating bootable USBs stated here: [http://swiss.ubuntuforums.org/showthread.php?t=1320738](http://swiss.ubuntuforums.org/showthread.php?t=1320738)

I think I can resolve the problem by loading the USB Startup Disk Creator as root. I tried ```
sudo startup-disk-creator
``` and other similar commands, but haven't managed yet. Does anyone know the command for the application (if there is one)?

Thanks,
Calixte

---

### Post by Calixte on 2009-11-11
I found the command. For the records here it is if anybody needs it:
On Ubuntu (Gnome)
```
sudo usb-creator-gtk
```
on Kubuntu (KDE)
```
sudo usb-creator-kde
```

---

### Post by fredfsh on 2011-05-03
Thanks. But it seems that I cannot provide the target device through command line and have to do so in a popped-out window. Is there a fully command-line tool?

---

### Post by MaGaM on 2012-05-03
Although the thread is already solved, could be handy to note that you can start the usb-creator-gtk with administrative rights by the command:
gksudo usb-creator-gtk.
That is what I used to create a 12.04 USB startup disk under 10.04 when starting it under a normal user and it asked for the password of 'root' (it actually should have asked for administrative privileges instead).

---

### Post by nothingspecial on 2012-05-03
Very old thread.

Closed.

---

