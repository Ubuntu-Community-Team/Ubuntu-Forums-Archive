---
title: "Computer won't stay in suspend"
date: 2012-03-17
forum: General Help
---

### Post by brandon89 on 2012-03-17
Hey so this happens randomly, but sometimes when I want to put my desktop in suspend it won't stay suspended.  It will turn off, but then a few seconds later (less than 5sec) it will turn on again.  It will continue doing this (me hitting suspend/the computer turning off & on) until I finally hold the power button in to turn the computer off.  I have to hold the power button because for some reason clicking on shut down doesn't do anything.

Thanks for any help!

I'm runnning Ubuntu 11.10 64-bit

---

### Post by Rebelli0us on 2012-03-17
USB3 will do that on some machines. There is a workaround if you google.


PS: If you have USB3, google "USB 3.0 workaround SUSPEND_MODULES=xhci-hcd"

---

### Post by 2F4U on 2012-03-17
You should start by looking into /var/log/pm-suspend.log. This log file contains many information about what happens during a suspend. Usually, one or more modules (usb, graphics, etc.) are responsible if a laptop unexpectedly wakes up from suspend  and you may be able to find out which by looking into the log file.

---

