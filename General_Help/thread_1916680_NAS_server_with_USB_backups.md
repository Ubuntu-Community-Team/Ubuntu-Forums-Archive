---
title: "NAS server with USB backups"
date: 2012-01-28
forum: General Help
---

### Post by skaber on 2012-01-28
Hello,
I'm running ubuntu on a server and I'd like to expand it's usage to be a NAS.
I'm basically planning to add 2 hard drives in RAID 1.

One thing I need, is the ability to make backups through USB. Thus, turn one USB port to USB Host mode and expose my harddrive to any device that connects on this port. Is this something doable? Do I need special hardware such as a motherboard that has USB Host mode in it's BIOS?

---

### Post by Lars Noodén on 2012-01-28
You can mount USB harddrives no problem, if that's what you're asking.  You can then use rsync to make the backup.

---

### Post by skaber on 2012-01-28
Thanks, but I want my TV receiver to mount the hard drive in my linux box, through USB.

So the linux server will act as a "USB drive".

---

