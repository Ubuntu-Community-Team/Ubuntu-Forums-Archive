---
title: "HELP! Can't overclock correctly - cannot set freq 16000[32000] to ep 0x86"
date: 2010-10-17
forum: General Help
---

### Post by 98cwitr on 2010-10-17
I am trying to get a stable overclock on my processor and if it's not set to exactly 3.2GHz or 2.66GHz (stock clock) I get this message. Using sysinfo, the OS does not register over 3.2GHz even when I have it clocked @ > 3.2

All the google searches and bug reports seem to talk about sound problems and webcam issues being the cause, but I've had this problem since I switched to Ubuntu and have not yet found a resolution. 

Specs in sig.

---

### Post by 98cwitr on 2010-10-17
> **98cwitr said:**
> I am trying to get a stable overclock on my processor and if it's not set to exactly 3.2GHz or 2.66GHz (stock clock) I get this message. Using sysinfo, the OS does not register over 3.2GHz even when I have it clocked @ > 3.2

All the google searches and bug reports seem to talk about sound problems and webcam issues being the cause, but I've had this problem since I switched to Ubuntu and have not yet found a resolution. 

Specs in sig.

fixed. It's related to my webcam...but adding the line

'acpi=off apm power_off=1' to etc/default/grub in the GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" line fixed my problem after a year of banging my head :guitar:


so the my line reads as such

```
GRUB_CMDLINE_LINUX_DEFAULT="acpi=off apm power_off=1 quiet splash"
```

---

### Post by dino99 on 2010-10-17
if you want your cpu, MB & ram hotter with full noisy fans, why not drop them in a 250° C oven

---

### Post by 98cwitr on 2010-10-17
> **dino99 said:**
> if you want your cpu, MB & ram hotter with full noisy fans, why not drop them in a 250° C oven

Im turning 28C...try again ;)

---

