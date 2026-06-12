---
title: "Driver help"
date: 2011-04-17
forum: General Help
---

### Post by r0llingthund on 2011-04-17
I have this issue when I boot up and shutdown 
The GUI right before it starts/stops running and takes me to a tty terminal then after a few seconds this appears in the login (and thanks to my phone I was able to take a picture of these errors)

> 
[14.199903] uvcvideo: uvcvideo: Failed to query (129) UVC probe control : -32 (exp. 26)
[14.199971] uvcvideo: Failed to initialize the device (-5)
[24.405693] /build/buildd/linux-2.6.35/drivers/hid/usbhid/hid-core.c: usb_submit_urb(ctrl) failed
I have been using Linux for a year and half now and I am usually able to work my way through problems but I have no Idea what this is. Please Help.

p.s. I am sorry if this is in the wrong thread but I don't usually post in forums

---

### Post by garvinrick4 on 2011-04-17
When you use a different kernel in grub menu entries what do you get?

---

### Post by r0llingthund on 2011-04-17
See thats the weird thing I only run one physical distro (ubuntu 10.10). I run Arch Linux and Back Track in a virtual machine. I never touch grub.

So when I press the power button It automatically takes me to the gnomes login manager (after the quick detour to the tty for some reason). Nothing is broken and everything is working fine. It's just that It says that there is an error and I can't just let that stay there, if you know what I mean.

---

### Post by garvinrick4 on 2011-04-17
I believe if you hold down shift key as you boot you will get the grub menu entries so as to
try a different kernel if wanted. It defaults to not stop at menu entry when only one O.S.

[LIST]
[*]**GRUB_HIDDEN_TIMEOUT=0**  on single operating system computers.
[LIST]
[*]No menu is displayed. The system is immediately booted to the default OS.
[*]This is the default setting with only one identified operating system.
[LIST]
[*]To display the menu under this condition, place a **#** symbol at the start of the line and ensure the GRUB_TIMEOUT setting is a positive integer.
[/LIST]
 
[*]If the value is set to **0**, a *keystatus* check is performed to determine if the *SHIFT* key is depressed. If GRUB 2 determines the *SHIFT*  key is depressed during the boot process, the menu will be displayed.  This gives the user a method of interrupting an automatic boot which  would normally not display the menu.
[*]Taken from:
[*][Grub2 - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Grub2#/etc/default/grub")
[/LIST]
 
[/LIST]

---

