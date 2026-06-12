---
title: "dvd rom tray closes automatically"
date: 2010-02-17
forum: General Help
---

### Post by santiagorf on 2010-02-17
Hi,
After I open the dvd rom tray either via ubuntu or by the eject button, it closes automatically.
I have two dvd drives insalled, but only one has this problem.
It's been a month that this problem started occurring, but it's not a hardware problem since both drives work fine in windows.

Any idea?
Thanks in advance
santiagorf

---

### Post by santiagorf on 2010-02-21
solved it
just
sudo sysctl -w dev.cdrom.autoclose=0

but the problem is I have to run this command every time I reboot my computer

---

### Post by AVH on 2010-03-01
I have the same problem. It started two releases ago when I got a SATA DVD drive. The 'sysctl' command doesn't work work for me even temporarily.

---

