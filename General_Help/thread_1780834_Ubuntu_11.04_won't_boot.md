---
title: "Ubuntu 11.04 won't boot"
date: 2011-06-12
forum: General Help
---

### Post by StrikeByte on 2011-06-12
I'm trying to run ubuntu 11.04 (64-bit) on my hp pavilion tx2100ed but it won't boot. After the grub bootscreen it goes black and doesn't react to Ctrl-Alt F1 ..F4.
Also booting the recovery mode doesn't work
To be able to start the installer I had to use xforcevesa.
Does any one know what this can be and how to solve it?

can i force x to start in vesa mode using grub commands?

thanks in advance

---

### Post by linuxinstalledfromhdd on 2011-06-12
Try using 10.10:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

That's might work. :)

---

### Post by Favux on 2011-06-13
Hi StrikeByte,

Welcome to Ubuntu forums!

It's the Xorg video driver.  If I remember correctly I used the *nomodeset* option on the kernel line.  When it boots or comes up there is an option to edit and you chose that and then add the option to the kernel line.  Then once you've booted into Ubuntu Natty use Additional Drivers to install/activate the proprietary Nvidia video driver.  Then reboot and it won't be a problem anymore.

---

### Post by StrikeByte on 2011-06-14
Thanks a lot that was what i was looking for (nomodeset)
Installed the driver and it all works now

---

