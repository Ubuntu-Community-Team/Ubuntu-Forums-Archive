---
title: "Cannot change date/time"
date: 2010-12-14
forum: General Help
---

### Post by yamada122 on 2010-12-14
Hi all,

I'm new to linux so please bear with me, I changed the date and time of my machine using **date**, it works, but if I reboot my machine, the date goes back as it was, I'm not connected to a time server, so.. what makes it go back ???

---

### Post by dcstar on 2010-12-15
> **yamada122 said:**
> Hi all,

I'm new to linux so please bear with me, I changed the date and time of my machine using **date**, it works, but if I reboot my machine, the date goes back as it was, I'm not connected to a time server, so.. what makes it go back ???

If you boot Windows it probably resets the time, otherwise the time in the BIOS is wrong.

---

### Post by sikander3786 on 2010-12-15
If you change the date/time using Clock from Panel, it gets changed for only a single session. You need Root previleges to change date/time. If you've not already done it this way, go to System > Administration > Time & Date, unlock and make changes there. Hope they'll be persistent.

---

