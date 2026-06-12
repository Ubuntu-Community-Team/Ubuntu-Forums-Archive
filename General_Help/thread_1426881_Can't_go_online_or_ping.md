---
title: "Can't go online or ping"
date: 2010-03-10
forum: General Help
---

### Post by buee on 2010-03-10
I feel stupid even posting this, but there's something severely wrong with this NAS.  It will not get network connectivity at all recently.  Can't ping, can't browse, no Samba, nothing.

I've checked my IP, mask, gateway, broadcast, network, and DNS settings and they're correct.  I've restarted networking, restarted the machine, nothing.  I've replaced the network card with a different brand and interface, nothing.

As I stated before, this is a NAS, so network connectivity is needed.

It's running Ubuntu 9.10 64-bit desktop.

Any helpful hints?

---

### Post by Iowan on 2010-03-10
Did it quit working - or has it ever? You've checked **sudo lshw -C network** to verify driver settings for the interface? Have you tried the cable connection on another machine to verify that it works?

---

### Post by buee on 2010-03-10
> **Iowan said:**
> Did it quit working - or has it ever? You've checked **sudo lshw -C network** to verify driver settings for the interface? Have you tried the cable connection on another machine to verify that it works?

The cable appears to be good.  Tested it with my macbook pro.  Tried that command, don't really know what I'm looking for.

EDIT: Scratch that, it may just be the cable.  For S&Gs I replaced the cable and it seem to be online, providing smb connections, pinging out, allowing VNC and SSH.  This thing has been running fine w/ 0 packet loss for months.  I'm still pinging though, we'll see what happens.

---

