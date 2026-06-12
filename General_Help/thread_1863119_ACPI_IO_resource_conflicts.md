---
title: "ACPI I/O resource conflicts"
date: 2011-10-17
forum: General Help
---

### Post by msx2 on 2011-10-17
Hi,
Whenever i start my server this reporTs the following errors:

[    5.273772] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x0c00
[    5.273783] ACPI: I/O resource 0000:00:02.1 [0xc00-0xc1f] conflicts with ACPI region SMRG [0xc00-0xc1f]
[    5.273786] ACPI: This conflict may cause random problems and system instability
[    5.273789] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver


Whats happens?

Thanks.

---

### Post by matt_symes on 2011-10-17
Hi

Sounds like you may have a buggy DSDT.

Try booting with the kernel command line option.
```

 acpi_enforce_resources=lax
```Do you have lm-sensors installed ?

Kind regards

---

### Post by msx2 on 2011-10-17
> **matt_symes said:**
> Hi

Sounds like you may have a buggy DSDT.

Try booting with the kernel command line option.
```

 acpi_enforce_resources=lax
```Do you have lm-sensors installed ?

Kind regards

Doesn't work... lm-sensors installed

Mobo: K7S5A Pro

---

### Post by matt_symes on 2011-10-17
Hi

Have you tried disabling acpi altogether ?

```
acpi=off
```Is it affecting your system ? Have you seen system instability ?

Have you tried blacklisting sis96x_smbus ?

Kind regards

---

### Post by msx2 on 2011-10-17
> **matt_symes said:**
> Hi

Have you tried disabling acpi altogether ?

```
acpi=off
```Is it affecting your system ? Have you seen system instability ?

Have you tried blacklisting sis96x_smbus ?

Kind regards

I have in blacklist the sis96x_smbus, but doesn't work.
I'm not interested to disabling acpi because i turn the server remotely.
I'm seeing lately that the server does not start right from the off, sometimes freezes on startup screen and memory test...

---

