---
title: "Cannot access XP taskbar in VirtualBox (fullscreen)"
date: 2010-05-21
forum: General Help
---

### Post by James78 on 2010-05-21
Hi,

Recently, I upgraded to VirtualBox 3.2.0, and I finally installed Windows XP Professional onto it. Anyways, have any of you noticed that when you set the VM to fullscreen, you cannot access the taskbar at all? The icon for the cursor reverts to my Linux cursor, showing that the focus switched to Linux somehow in someway. The taskbar is set to always show, and this happens at the EXACT pixel that the panel starts at. It's pretty annoying if I say so myself.

Forgot to mention, that this only happens with the mouse integration, and not mouse capture (for obvious reasons).

Does anyone have any similar symptoms?

Using: Windows XP Professional 32-bit (guest, and running SP3 with all updates) on VirtualBox 3.2.0 hosted by Ubuntu 10.04 64-bit (using KDE).

---

### Post by JoelOl75 on 2010-05-21
Did you reinstall the guest additions for the new version?  Might be the problem.

---

### Post by James78 on 2010-05-21
I installed XP when it was upgraded to 3.2.0, and it already has 3.2.0 guest additions. I reinstalled it once before I found out this problem, I'll uninstall, restart, reinstall, and restart, then see if that caused any problem, but I highly doubt it.

Edit: Nope, problem still there.

---

### Post by theozzlives on 2010-05-21
select resize guest display to fit window, I think it's under the machine menu.

---

### Post by James78 on 2010-05-21
That option doesn't exist... I think at this point, I'm inclined to believe it's a bug though..

---

### Post by theozzlives on 2010-05-21
> **James78 said:**
> That option doesn't exist... I think at this point, I'm inclined to believe it's a bug though..

Sorry, it's auto-resize guest display

---

### Post by James78 on 2010-05-21
Lol, you meant maximize the window with auto resize guest display didn't you. Anyways, ya, it seems I'll have to do that as a "workaround" for now. I reported the bug, so hopefully it'll get fixed sometime.

---

### Post by tapeloopghost on 2011-10-22
I'm using Debian, but I am having this exact same problem. Did anyone ever figure out a solution?

---

