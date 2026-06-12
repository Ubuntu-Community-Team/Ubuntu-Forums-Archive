---
title: "Repeated switching to-from TTY causes Karmic freeze"
date: 2010-03-20
forum: General Help
---

### Post by jcoles on 2010-03-20
In my Karmic (32-bit) installation, switching between Ctrl-Alt-F[1-6] and Gnome (Ctrl-Alt-F7) more than a few times can lead to a blank screen total freeze. There is no response to any keystrokes and the computer does not respond to pings on the network.

I have experienced this with both GDM and XDM.

The only way out is to turn the machine off and restart. Often this causes alarming messages about /dev/sda2 (my /home partition, system is sda1) having errors and not being able to mount. After fsck spends a few minutes checking/repairing the partition, the system can resume. Everything seems normal afterwards.

No logs that I have examined show error messages at the time of the freeze. The system simply stopped dead in its tracks.

---

