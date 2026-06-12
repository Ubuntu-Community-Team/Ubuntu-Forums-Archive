---
title: "I have deleted the resolv.conf folder. How can I write new one?"
date: 2010-05-01
forum: General Help
---

### Post by johnnymenmonic on 2010-05-01
Hi,

unfortunately I have deleted with sudo the resolv.conf folder in /etc/. How can I write a new one? What files contains your resolv.conf folder?

---

### Post by dcstar on 2010-05-01
> **johnnymenmonic said:**
> Hi,

unfortunately I have deleted with sudo the resolv.conf folder in /etc/. How can I write a new one? What files contains your resolv.conf folder?

[LIST=1]
[*]Try reinstalling the **avahi-daemon** package
[*]Don't be so stupid as to delete system files next time.
[/LIST]

---

### Post by johnnymenmonic on 2010-05-01
Thank you this works. But I am a bit worried, because there are no files inside /etc/resolvconf/update-libc.d. Is there something wrong with it? Or maybe there will be new files when I reboot my system?

---

### Post by wnelson on 2010-05-01
Another way is to:
#ifdown eth0
#ifup eth0

#/etc/init.d/network start

---

