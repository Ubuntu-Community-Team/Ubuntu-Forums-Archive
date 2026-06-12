---
title: "PS2 Mouse not working after upgrade to 12.04"
date: 2012-05-13
forum: General Help
---

### Post by rjcharron on 2012-05-13
I recently upgraded my system from 11.10 to 12.04 LTS. I have logitech PS2 mouse and keyboard. Keyboard works fine, mouse does not. As soon as X11 is active, mouse cursor is stuck to left edge of screen. It can move up and down along left edge, but will not move anywhere else on the screen. The update did install a new /etc/X11/xorg.conf which now says keyboard settings are read from /etc/default/console-setup. I can't see anything there that concerns the mouse. I also tried a USB mouse and a USB wireless mouse - the same problem persists.

I've seen a few postings indicating others have had this issue but cannot find posts relating a solution to the problem.

Any help would be much appreciated. Pls keep in mind I can only use the system in terminal mode.

---

### Post by theducks on 2012-05-17
12.04
My Ps2 Logitec Mouse and PS2 IBM Keyboard would not respond onve the Logon screen appeared.
(Keyboard worked to select Ubuntu in Grub2: Dual boots with XP)

Resolution: Disconnected other USB HID (Mouse and Tablet) that were attached.

---

