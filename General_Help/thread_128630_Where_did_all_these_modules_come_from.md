---
title: "Where did all these modules come from?"
date: 2006-02-11
forum: General Help
---

### Post by squirrelplayingtag on 2006-02-11
I've been trying to speed up my system some so I decided to see what modules I had loaded. Well I have a ton, most of which I'm not using such as bluetooth, pcc_acpi, battery stuff, etc. But I can't figure where they are being loaded at! I have 3 entries in my /etc/modules so I know they are not loaded there. Little help?

---

### Post by az on 2006-02-11
[QUOTE=squirrelplayingtag]I've been trying to speed up my system some so I decided to see what modules I had loaded. Well I have a ton, most of which I'm not using such as bluetooth, pcc_acpi, battery stuff, etc. But I can't figure where they are being loaded at! I have 3 entries in my /etc/modules so I know they are not loaded there. Little help?[/QUOTE]

When you boot, the initrd detects some hardware and loads the modules for you.  I think it still uses discover.  Once the initrd is exited, your system boots and hotplug detects and loads more modules.

I doubt you will be able to speed up your system by preventing modules from being loaded.  At best, you can recompile your kernel with the modules buil-in statically, but that would probably only save on boot time.  I don't think it is a good way to improve performance.

Years ago, before hardware detection at boot time, kernel were built with tond of options so that they would run on a lot of different hardware.  That would make them run slower.  This is not the case anymore.  Modules are more or less loaded on-demand.

---

