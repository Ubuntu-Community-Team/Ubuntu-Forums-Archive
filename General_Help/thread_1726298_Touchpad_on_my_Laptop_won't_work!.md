---
title: "Touchpad on my Laptop won't work!"
date: 2011-04-10
forum: General Help
---

### Post by Dangerzone812 on 2011-04-10
Hey all, I just put ubuntu 10.10 on my HP Pavilion dv9000, and it's been working well for the past few days, but just recently the touch pad stopped working, even when it's on. My usb connected mouse works. What should I do?! I need this resolved now.

Thanks in advance,

Danger.

---

### Post by Dangerzone812 on 2011-04-11
Hello? :(

---

### Post by DeMus on 2011-04-11
> **Dangerzone812 said:**
> Hello? :(

Can you boot your laptop with a live-cd and test if the touchpad works, just to rule out a hardware problem.

---

### Post by Dangerzone812 on 2011-04-11
Just booted up from a liveUSB, seems to work. I mean, my touch pad works on the login screen, it's when it starts to load up my desktop that the touch pad stops working. :\

---

### Post by Dangerzone812 on 2011-04-11
Anyone? :\

---

### Post by sc4s2cg on 2011-04-24
I have the same exact problem.

Live does work, even after login. Running Ubuntu straight from the HD though, the touchpad only works at login and not afterwards.

---

### Post by sc4s2cg on 2011-04-24
This worked for me, check it out:

[quote=Troubleshooting]This usually happens when you disable your touchpad and then suspend your computer. To fix this just run this command:

gconftool-2 --set --type boolean /desktop/gnome/peripherals/touchpad/touchpad_enabled true

If nothing else works, see the other touchpad debugging pages.

[/quote]
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

---

### Post by KegHead on 2011-04-24
Hi!

Have you tried;

software center.."touchpad"?

KegHead

---

