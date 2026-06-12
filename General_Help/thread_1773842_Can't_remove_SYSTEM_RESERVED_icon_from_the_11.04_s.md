---
title: "Can't remove SYSTEM RESERVED icon from the 11.04 shortcut bar. [HELP]"
date: 2011-06-02
forum: General Help
---

### Post by Mt_Olympus on 2011-06-02
Hello,

I'm having an issue with removing an icon named "SYSTEM RESERVED" from the new 11.04 shortcut bar on the left side of the screen. If theres a specific name for it I don't know it. I had shortcut of the same name on my desktop and was unable to remove but found a forum with directions on how to fix it, but not one for the shortcut bar. So here I am. Can someone help me fix this? It would be much appreciated! One more thing, the icon looks like a hard drive.:rolleyes:

---

### Post by LowSky on 2011-06-02
it is a hard drive partition. for your Windows Files. I recommend you keep it on the task bar.

---

### Post by Mt_Olympus on 2011-06-02
Thanks for the advice :D

---

### Post by LowSky on 2011-06-02
Just move it to the very bottom, out of sight, out of mind.

---

### Post by coffeecat on 2011-06-02
If you have an icon named "System Reserved" on your launcher, then a partition with that partition label is being mounted on bootup. Which is not a good idea. And ignoring it or forgetting about it is not a good idea either. It is either your Windows recovery partition or your Windows 7 boot partition (if you have Windows 7). It is very inadvisable  to mount either of these except for very special reasons.

Have you, by chance installed the [s]abomination[/s] application called ntfs-config? Have you by chance used it?

> **Mt_Olympus said:**
> One more thing, the icon looks like a hard drive.:rolleyes:

Yes, well it would. All mounted partitions are shown with hard drive icons.

---

### Post by Mt_Olympus on 2011-06-02
Thanks for the advice. But the issue has been fixed. For some reason the icon went away after I restarted my machine.

---

### Post by coffeecat on 2011-06-02
> **Mt_Olympus said:**
> But the issue has been fixed. For some reason the icon went away after I restarted my machine.

Interesting. The partition would appear in the left "Places" pane of a nautilus window, but unmounted. It is easy enough to accidentally mount it though by inadvertently clicking on it. Perhaps this is what happened. To get a partition mounted automatically on bootup, you have to add a line to the configuration file /etc/fstab, which is not something that happens accidentally (unless you install ntfs-config :p) and a mount line in fstab doesn't disappear spontaneously, so if the icon went away of its own accord we can assume that fstab is not involved.

Post back if you have any more troubles with this. I have the thread subscribed. And good luck with using Ubuntu!

---

