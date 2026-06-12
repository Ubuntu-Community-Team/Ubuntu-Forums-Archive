---
title: "Mouse not working"
date: 2010-01-23
forum: General Help
---

### Post by Joey B. on 2010-01-23
My mouse isn't working when I plug it in, it's a USB Logitech Wireless Mouse and it doesn't work unless I boot with it plugged in then it stops working eventually.

---

### Post by chinaCat86 on 2010-01-23
what does dmesg | tail have to say?

I had similar issue the other week. It would respond with Failed to enumerate USB device on Port X or something similiar over and over. Never really found an issue after a few days of non use I randomly tried pluging in my wireless MS mouse and my wireless Logitech keyboard and they have been working for the past 24 hrs.

---

### Post by Joey B. on 2010-01-23
> **chinaCat86 said:**
> what does dmesg | tail have to say?

I had similar issue the other week. It would respond with Failed to enumerate USB device on Port X or something similiar over and over. Never really found an issue after a few days of non use I randomly tried pluging in my wireless MS mouse and my wireless Logitech keyboard and they have been working for the past 24 hrs.

Well, I get no error, it just doesn't activate. It acts as though nothing is plugged in.

---

### Post by chinaCat86 on 2010-01-23
have you tried using it on another machine or changing the port you plug the device into. Also, if you have any other OS installed perhaps boot into that and see if the mouse works. I suppose try and narrow things down a bit. Or wait for someone to come a long who knows what they are talking about.

---

### Post by Joey B. on 2010-01-23
My mouse works fine when I run Windows 7, it just doesn't work here on Ubuntu, no matter what the port.

---

### Post by Sef on 2010-01-23
1) Do you have another computer you can plug it into?  Could be the mouse is going bad.

2) From the terminal (Applications > Accessories > Terminal), make sure the mouse is plugged in and copy and paste this code:  ```
lsusb
```  Copy and paste the results there.

---

### Post by Joey B. on 2010-01-23
>  joey@joey-laptop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b027 Chicony Electronics Co., Ltd Gateway USB 2.0 Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
joey@joey-laptop:~$ ^C
joey@joey-laptop:~$ 

There.

---

### Post by Joey B. on 2010-01-23
I really need help with this because my left mouse button is broken and I hate having to double tap.

---

