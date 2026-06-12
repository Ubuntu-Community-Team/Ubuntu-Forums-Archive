---
title: "No S3, only S4 (Ubuntu 11.04)"
date: 2011-05-21
forum: General Help
---

### Post by joostp on 2011-05-21
Hello,

I'm having troubles getting my HTPC to use 'suspend-to-ram'.
I have a Asrock 760GM-GS3 motherboard. In the bios settings I have set 'suspend to ram ' to 'auto' (the only two options are auto and disabled).

I'm running Ubuntu 11.04 and in power management I have set the suspend button to 'suspend'.

What I find strange is that my 'cat /proc/acpi/wakeup' output only lists S4, not S3.
Is this a sign that there is a problem with S3 in my setup?


```
Device	S-state	  Status   Sysfs node
PCE2	  S4	*enabled   pci:0000:00:02.0
PCE3	  S4	*disabled  
PCE4	  S4	*disabled  
PCE5	  S4	*enabled   pci:0000:00:05.0
PCE6	  S4	*disabled  
PCE7	  S4	*disabled  
PCE9	  S4	*disabled  
PCEA	  S4	*disabled  
PCEB	  S4	*disabled  
PCEC	  S4	*disabled  
SBAZ	  S4	*enabled   pci:0000:00:14.2
UAR1	  S4	*enabled   pnp:00:0a
P0PC	  S4	*disabled  pci:0000:00:14.4
UHC1	  S4	*enabled   pci:0000:00:12.0
UHC2	  S4	*enabled   pci:0000:00:12.1
UHC3	  S4	*enabled   pci:0000:00:12.2
USB4	  S4	*enabled   pci:0000:00:13.0
UHC5	  S4	*enabled   pci:0000:00:13.1
UHC6	  S4	*enabled   pci:0000:00:13.2
UHC7	  S4	*enabled   pci:0000:00:14.5
```

---

### Post by joostp on 2011-05-22
I just reverted to Ubuntu 10.10 and I have the same output.
Is this a conflict between Ubuntu and my motherboard?

---

### Post by joostp on 2011-05-22
Anybody?

---

