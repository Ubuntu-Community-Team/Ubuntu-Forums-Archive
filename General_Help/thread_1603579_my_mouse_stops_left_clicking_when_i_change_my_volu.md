---
title: "my mouse stops left clicking when i change my volume with my keyboard"
date: 2010-10-22
forum: General Help
---

### Post by Renegade13 on 2010-10-22
when i change my volume via the buttons on my keyboard, my left click on my mouse just stops working, then i have to restart my computer to get it to work again. anyone now a fix or a workaround for this?

---

### Post by adw404 on 2010-10-27
I have the same problem. After using the calculator button, volume buttons, media control buttons, email, home page or IM buttons, the mouse will not register mouse clicks anymore. The problem can be solved by restarting, as said above, or by unplugging and replugging the USB receiver. The problem only started after upgrading to 10.10. Using Ubuntu 10.10 64bit, Microsoft Wireless Mouse 5000, Microsoft Wireless Keyboard 3000 v2.0, there is one receiver for both mouse and keyboard.

---

### Post by sheamuso on 2010-11-23
I have the same problem with Meerkat, 64 bit AMD chip and Microsoft 600 keyboard. Can't remember having problems on 32 bit, ubuntu 7.04 - 10.04.

All of the multimedia buttons (play/pause, volume, mute) "stop left click"on my mouse.

The mouse is a standard Dell OEM.

I can get the button to work again by pulling the keyboard usb cable and mouse usb cable out at the same time and plugging them back in.

Let me know if you want me to report more information.


Sheamus OHalloran

---

### Post by blackmonk on 2010-11-25
I see a few threads have been created about this issue, but i wanted to add my voice to this too.
I have a MS keyboard/mouse combo 3000 V2. The special keys worked fine in kubuntu 10.04, but in ubuntu 10.10 I have the same difficulty as the people above. When I use the special keys (including the volume buttons) the left mouse button stops working. 

Also, as above, restarting the computer or removing the USB wireless dongle fixes this. 

Perhaps of interest - I am using a different wireless mouse, and have found that removing the keyboard USB wireless dongle fixes the issue. Removing the mouse wireless key does not.

Edit - I found a bug discussion that had a temp fix that works for me. The bug dicussion can be found at:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/636311](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/636311)

And the solution (described in the link above) was to add  a PPA to the Software Sources, and then apt-get update and apt-get upgrade. When I restarted X, I can now use my special keys and not lose the function of my left mouse button.
[https://launchpad.net/~raof/+archive/aubergine/](https://launchpad.net/~raof/+archive/aubergine/)

---

