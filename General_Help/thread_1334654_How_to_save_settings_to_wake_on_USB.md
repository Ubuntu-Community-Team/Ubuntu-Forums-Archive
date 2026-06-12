---
title: "How to save settings to wake on USB?"
date: 2009-11-22
forum: General Help
---

### Post by Superorb on 2009-11-22
I'm able to wake the PC via USB, but once I reboot or power off/on the PC the settings are not saved. I originally enabled the USB wake funcion with the following:

```

echo USB1 > /proc/acpi/wakeup

```

Is there a way to have the settings remembered each time I cycle the box?

---

### Post by dcstar on 2009-11-23
> **Superorb said:**
> I'm able to wake the PC via USB, but once I reboot or power off/on the PC the settings are not saved. I originally enabled the USB wake funcion with the following:

```

echo USB1 > /proc/acpi/wakeup

```

Is there a way to have the settings remembered each time I cycle the box?

Put it in /etc/rc.local

---

### Post by Superorb on 2009-11-23
> **dcstar said:**
> Put it in /etc/rc.local
Thanks much!!

---

