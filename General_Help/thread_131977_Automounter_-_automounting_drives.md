---
title: "Automounter - automounting drives"
date: 2006-02-17
forum: General Help
---

### Post by zappa86 on 2006-02-17
Hi. Does anyone know about the automounter, or whatever its called that automounts disks and such. When I plug in flashdrives to my computer, or a regular USB HD, or put in a CDROM it wont auto mount it. Ive restarted my computer and still nothing happens. Each time I want to mount a device I must go to a root shell and mount /dev/device /media/mntpoint -o uid=1000 and do all that stuff. Does anyone know how to re-enable the automounter and how to configure it so it will always mount stuff. thanks.

---

### Post by dcstar on 2006-02-17
[QUOTE=zappa86]Hi. Does anyone know about the automounter, or whatever its called that automounts disks and such. When I plug in flashdrives to my computer, or a regular USB HD, or put in a CDROM it wont auto mount it. Ive restarted my computer and still nothing happens. Each time I want to mount a device I must go to a root shell and mount /dev/device /media/mntpoint -o uid=1000 and do all that stuff. Does anyone know how to re-enable the automounter and how to configure it so it will always mount stuff. thanks.[/QUOTE]
What does System-Preferences-Removable Drives and Media show?

Run "dmesg" when you insert stuff and look at the messages.

---

