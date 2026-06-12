---
title: "Wake from sleep using keyboard with integrated trackball"
date: 2010-03-05
forum: General Help
---

### Post by nunovi on 2010-03-05
Hi,

I have a nettop which I currently connect to my HDTV. I've successfully configured ubuntu to wake from sleep whenever I press a key or move the mouse and that's working perfectly. The issue for me is that I'm using a keyboard with an integrated trackball. The trackball is sensitive enough to detect a small movement when I put the keyboard on the sofa, causing for the computer to wake up.
I've tried disabling usbhid module and loading usbkbd when I suspend but, although the mouse is disabled in Ubuntu, it still sends events to the USB port, causing the computer to resume. And since it's the same USB port for keyboard and mouse, disabling the port is not going to work, as it would disable both keyboard and mouse.

Ideally, I would like to resume the computer only when a certain key is hit. I recon this is probably done at BIOS level, so not sure if this is remotely possible.

Anyone has any thoughts on how to achieve this?

Thanks for your help,

Nuno

---

