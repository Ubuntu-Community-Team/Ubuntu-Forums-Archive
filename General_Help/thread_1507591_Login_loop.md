---
title: "Login loop"
date: 2010-06-11
forum: General Help
---

### Post by Chaos_Spear on 2010-06-11
So I've read a bunch of the other login loop threads, but they haven't seemed to help me.  I'm running 10.04, which was great until this.  I read [http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=9321636&postcount=2](http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=9321636&postcount=2), which gave me some clues as to what might be wrong, but still at a loss at how to fix it.

My situation is this: I first get a low-res kubuntu startup screen, which eventually goes away, and I get my normal login screen(low-res when I don't try booting with Free Software Only) but (a) the system stutters every few minutes (temporary freeze) and (b) the login button won't work.  After a few minutes of pressing "Login" I get an "Authentication Failed" message.

When I try Console Login, I get inundated with messages usually saying things like "ata1.00: status: {DRDY ERR}" and "b43-phy0 ERROR: Fatal DMA error:" and still can't login.

Any suggestions?  Please, I'm leaving on a long trip tomorrow and want my laptop... which is a Dell Inspiron 1545, btw.

---

### Post by Chaos_Spear on 2010-06-11
Please help!

---

### Post by jv2112 on 2010-06-11
Sounds like a HD error. Have you run any diagnostics on the drive ?

---

### Post by Chaos_Spear on 2010-06-11
> **jv2112 said:**
> Sounds like a HD error. Have you run any diagnostics on the drive ?

The system runs a fsck and comes back clean.  I'll try doing one from the Live CD but I don't think that's the problem...

---

### Post by Chaos_Spear on 2010-06-11
BTW sorry I forgot, this happened after activating some proprietary drivers and rebooting, but still happens when running "Free Software Only"

---

### Post by Chaos_Spear on 2010-06-11
Ended up doing a clean re-install.  Thanks anyways.

---

