---
title: "disable a process at boot"
date: 2009-11-26
forum: General Help
---

### Post by viralmeme on 2009-11-26
I have these processes running at boot, how to disable please, assuming they don't do anything vital. It's on a USB device so I don't need cron, or modem-manager ..?

$ps -ef

root      3069     1  0 13:54 ?        00:00:00 /usr/sbin/modem-manager
ubuntu    4404     1  0 13:54 ?        00:00:00 gnome-screensaver
root      3625     1  0 13:54 ?        00:00:00 cron
root      3557     1  0 13:54 ?        00:00:00 /sbin/wpa_supplicant -u -s
root      3558     1  0 13:54 ?        00:00:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      4460  4459  0 13:55 ?        00:00:00 devkit-disks-daemon: polling /dev/sdb /dev/sr0
--

Xubuntu 9.10, USB startup disk creator

---

### Post by mkvnmtr on 2009-11-26
You might go to Startup Applications and then to services. They are both under System.

---

### Post by viralmeme on 2009-11-26
> **mkvnmtr said:**
> You might go to Startup Applications and then to services. They are both under System.
Sorry, not there. I'm using Xfce and Boot up Manager. I installed and uninstalled 'freenet' and then these new processes turned up.

---

