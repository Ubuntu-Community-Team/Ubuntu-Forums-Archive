---
title: "gdm login banner"
date: 2010-02-09
forum: General Help
---

### Post by GovDude on 2010-02-09
Our corporate policy requires that a login banner be displayed. In the past I've set InfoMsgFile=<filename> and voila my banner is displayed and users even have to click OK to get past it.

With 9.10 that's not working. I've set the exact same thing in /etc/gdm/custom.conf but it seems to be totally ignored.

I've used gconf-editor to set apps/gdm/simple-greeter/banner_message_enable to Mandatory and the same thing for disable_user_list and still no luck.

Any ideas?

TIA

---

### Post by amac777 on 2010-02-09
Did you reboot after you made the change in /etc/gdm/gdm.conf? I'm on 9.04 so maybe that is not the issue but it took a reboot before it started working.

---

### Post by GovDude on 2010-02-10
Yep. Rebooted multiple times, and restarted gdm several times.

---

