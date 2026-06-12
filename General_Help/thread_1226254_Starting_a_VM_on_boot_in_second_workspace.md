---
title: "Starting a VM on boot in second workspace?"
date: 2009-07-29
forum: General Help
---

### Post by Xero Xenith on 2009-07-29
I currently have a VirtualBox installation of Windows XP that I'd like to start on boot in full screen on my second workspace (I have two - left and right). Can this be done?

Huge thanks in advance for any answers :)

(Running Ubuntu Jaunty 64-bit, fully updated.)

---

### Post by mindo on 2009-07-29
Hi,

You can go to System -> Preferences -> Startup Applications then press Add and the command type

```
VBoxManage startvm <VM name>
```

To make it load always on the same workspace, take a look into [this]("http://ubuntu-tutorials.com/2007/07/25/how-to-set-default-workspace-size-and-window-effects-in-gnome/") howto.




Cheers

---

### Post by Xero Xenith on 2009-07-29
Wow, thanks a lot :D much appreciated :)

---

