---
title: "Ubuntu boot time on imac"
date: 2010-05-24
forum: General Help
---

### Post by chrissk_2 on 2010-05-24
Hi all,

i have a 24'' imac core duo 2 (2007 model) 4GB ram, nvidia 7600

I recently installed lucid and everything worked perfectly. The boot times where 14.5 secs on a clean installation. I even enabled the xorg-edgers repo and nouveau with 3d was working almost perfectly. The boot time was around 20-23 secs with compiz enabled and 2.6.34-2 kernel installed from xorg-edgers.

What i tried next was to manually compile the 2.6.34 kernel and statically link all drivers, to improve performance and boot time a bit. This also worked fine and the system works ok.

However, i did not see any improvements during boot (around 20 secs) and there is a huge gap of 10 second from the time the kernel initializes usb until udev is started. The logs are completely empty.

The build has only the necessary drivers. Can someone explain what is happening and if there is a way to improve on that ?
Are there any kernel options or tools i can use to get more info on what is happening during this period ?

I attach my kernel config, a dmesg log and the boot chart png

Thanks in advance

---

