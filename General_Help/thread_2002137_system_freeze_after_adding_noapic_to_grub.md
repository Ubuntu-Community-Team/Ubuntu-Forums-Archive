---
title: "system freeze after adding noapic to grub"
date: 2012-06-12
forum: General Help
---

### Post by yasr on 2012-06-12
I have an issues on which your expert knowledge is required so that I can solve it, here is the scenario:

[Problem was] Sticky mouse after installation!

To solve this issues I did following procedure:

gksudo gedit /etc/default/grub
added "noapic acpi=noirq nolapic" to the end of CMD_LINUX_Defualt line
ran: "sudo update-grub" and rebooted.
This solved my sticky mouse problem. After that, I installed a mobile broadband, connected it and the connection was established. I opened firefox and probably after 3 or 5 mins, the system froze down. I rebooted it. Now the mobile broadband connection option had disappeared from menu.

The problem is: How do I configure ubuntu so that it does not freezes on using mobile broadband via usb port?

P.S. I have recently switched from Microsoft OS to linux ubuntu

Your kind opinions will highly be appreciated.

Regards,

---

