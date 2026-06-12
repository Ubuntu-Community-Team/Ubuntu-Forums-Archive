---
title: "Turn off graphical shutdown"
date: 2010-09-30
forum: General Help
---

### Post by dismas on 2010-09-30
I want to see the scrolling console messages when Ubuntu shuts down instead of the 4 dot splash animation. Is this possible, and how can I do it?

---

### Post by yetiman64 on 2010-09-30
> **dismas said:**
> I want to see the scrolling console messages when Ubuntu shuts down instead of the 4 dot splash animation. Is this possible, and how can I do it?

One way would be to edit /etc/default/grub and remove the "quiet" and "splash" entries from the "GRUB_CMDLINE_LINUX_DEFAULT=" line. This will give scrolling text in the startup and shutdown sequences (so don't know if it is exactly as you want).

Before editting /etc/default/grub please do a backup first with
```
sudo cp /etc/default/grub /etc/default/grub.bak
```Then use
```
gksudo gedit /etc/default/grub
``` and edit the line mentioned above. Then use
```
sudo update-grub
``` to make the new settings take hold.
Reboot the machine and text will be visible on next startup and shutdown.
When removing the quiet and splash entries leave the quotation marks "" (even if they are all that are left).

Note that this method removes the splash screen at BOTH startup and shutdown.

---

