---
title: "broadcom wireless driver install not working in latest kernel..."
date: 2012-10-13
forum: General Help
---

### Post by karasuman on 2012-10-13
I'm following the instructions [here]("http://www.broadcom.com/docs/linux_sta/README.txt") to install whatever my wireless card needs to function.  The latest kernel build in which I can get both my wireless and my nvidia graphics card to work ends in .40.

Following these instructions in the latest build results in the following error: "insmod: error inserting 'wl.ko': -1 invalid module format"

Any advice?  Also, I think I found a way to include updates to the nvidia driver in the general update search; is there any way to do this with broadcom drivers?  It's very frustrating, because it seems that my wireless breaks every single time I update to a new version of the kernel.  Even when I get the wireless working, I usually have to use terminal commands to get it going if I restart my machine.

I'm still using 10.4, by the way.  It doesn't sound like updating to the newest flavor of ubuntu will do anything to ameliorate this situation, and I know it will do plenty of things to **** me off, so I'm sticking with the LTS for the time being.

---

### Post by Rexilion on 2012-10-13
Please provide the output of:

> dmesg
lspci -v
uname -a

Also, please do this after you entered the command which gave the error referring to 'invalid module format'.

---

