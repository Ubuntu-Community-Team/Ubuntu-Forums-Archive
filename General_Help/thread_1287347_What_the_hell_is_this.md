---
title: "What the hell is this?"
date: 2009-10-10
forum: General Help
---

### Post by baskar007 on 2009-10-10
i am new to ubuntu,
i am using 9.04janty

My PC won't shutdown.
Whenever i try to shutdown it will display somting like this:
> md: stopping all md devices
sd 1:0:0:0: [sda] Synchronizing SCSI
sd 1:0:0:0: [sda] Stopping disk
r8169 0000:01:00.0: PME# enabled
system halted


If any one knows what is this please tell me.:confused:

---

### Post by lisati on 2009-10-10
My first thought: check your BIOS to see if you have power management switched on.

---

### Post by baskar007 on 2009-10-10
> **lisati said:**
> My first thought: check your BIOS to see if you have power management switched on.
yes just i checked, Power management is enabled on my BIOS.

---

### Post by sloggerkhan on 2009-10-10
> **baskar007 said:**
> i am new to ubuntu,
i am using 9.04janty

My PC won't shutdown.
Whenever i try to shutdown it will display somting like this:



If any one knows what is this please tell me.:confused:


If it says system halted, usually that means you can turn off the power manually. And that for some reason it can't cut power itself, or the option to wasn't passed to the shutdown command. I think. (Not 100% sure about this, check man page for shutdown.

---

### Post by baskar007 on 2009-10-10
> **sloggerkhan said:**
> If it says system halted, usually that means you can turn off the power manually. And that for some reason it can't cut power itself, or the option to wasn't passed to the shutdown command. I think. (Not 100% sure about this, check man page for shutdown.
ya every time i wait for ubuntu shutdown fully and then i switch of the power.
there is now way to solve this problem?

---

### Post by sloggerkhan on 2009-10-10
what happens with 
```

sudo shutdown -P now

```
?

---

### Post by baskar007 on 2009-10-10
> **sloggerkhan said:**
> what happens with 
```

sudo shutdown -P now

```?
same issue is present.

system halted

---

### Post by sloggerkhan on 2009-10-10
As noted by previous poster, 
check out what
r8169 0000:01:00.0: PME# enabled
means.
r8169 is probably a wireless networking chip (or maybe a wired networking chip), though I don't know that for sure. It may be stuck in a mode that's locking your system from a full shutdown or something.

File a bug report.

---

### Post by SkyNet2029 on 2009-10-10
for a power down on shutdown, the switch of -p is passed, like thus:
 
```
#halt -p
```
 
this would cause the system to shutdown grracefully, calling a power down at completion of the graceful shutdown event.

---

### Post by garvinrick4 on 2009-10-10
To reboot try alt/sys rq/b in that order.  Should restart.  let me know if does not.

---

### Post by prshah on 2009-10-10
> **baskar007 said:**
> 
My PC won't shutdown.

Probably an ACPI issue; open a terminal (Applications-accessories-Terminal) and post the output of the command ```
dmesg |grep -i acpi
```

Does your computer have a "soft-off" button? How old/new is it? What config?

---

### Post by P4man on 2009-10-10
ACPI is not working. Either its not enabled in the bios, or its disabled in the kernel (possibly because its a known buggy bios?). If you are sure you have it enabled in the BIOS, you can try forcing it by adding "acpi=force" to your kernel options.

---

### Post by baskar007 on 2009-10-10
> **prshah said:**
> Probably an ACPI issue; open a terminal (Applications-accessories-Terminal) and post the output of the command ```
dmesg |grep -i acpi
```

Does your computer have a "soft-off" button? How old/new is it? What config?
here is the output:
> -desktop:~/Documents$ dmesg |grep -i acpi
[    0.000000]  BIOS-e820: 000000003f7f0000 - 000000003f7fe000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f7fe000 - 000000003f800000 (ACPI NVS)
[    0.000000]  modified: 000000003f7f0000 - 000000003f7fe000 (ACPI data)
[    0.000000]  modified: 000000003f7fe000 - 000000003f800000 (ACPI NVS)
[    0.000000] ACPI: RSDP 000F94F0, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 3F7F0000, 0034 (r1 011509 RSDT1935 20090115 MSFT       97)
[    0.000000] ACPI: FACP 3F7F0200, 0084 (r2 011509 FACP1935 20090115 MSFT       97)
[    0.000000] ACPI: DSDT 3F7F0430, 4DBB (r1  z945c z945c010       10 INTL 20051117)
[    0.000000] ACPI: FACS 3F7FE000, 0040
[    0.000000] ACPI: APIC 3F7F0390, 005C (r1 011509 APIC1935 20090115 MSFT       97)
[    0.000000] ACPI: MCFG 3F7F03F0, 003C (r1 011509 OEMMCFG  20090115 MSFT       97)
[    0.000000] ACPI: OEMB 3F7FE040, 0061 (r1 011509 OEMB1935 20090115 MSFT       97)
[    0.000000] ACPI: no DMI BIOS year, acpi=force is required to enable ACPI
[    0.000000] ACPI: Disabling ACPI support
[    0.278848] ACPI: Interpreter disabled.
[    0.280276] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    0.284092] pnp: PnP ACPI: disabled

---

### Post by baskar007 on 2009-10-10
> **sloggerkhan said:**
> As noted by previous poster, 
check out what
r8169 0000:01:00.0: PME# enabled
means.
r8169 is probably a wireless networking chip (or maybe a wired networking chip), though I don't know that for sure. It may be stuck in a mode that's locking your system from a full shutdown or something.

File a bug report.
Ya iam using wireless modem for internet

---

### Post by baskar007 on 2009-10-10
> **P4man said:**
> ACPI is not working. Either its not enabled in the bios, or its disabled in the kernel (possibly because its a known buggy bios?). If you are sure you have it enabled in the BIOS, you can try forcing it by adding "acpi=force" to your kernel options.
ok i will check for that acpi.

thanks you for your reply's. and sorry for late response due to network problem.

---

### Post by Tony Flury on 2009-10-10
> **baskar007 said:**
> here is the output:
```

[ 0.000000] ACPI: no DMI BIOS year, acpi=force is required to enable ACPI

```


There you go - your kernel is not recognising the ACPI capability in your BIOS.

You will need to add "acpi=force" to your kernel start up command - i would try it from the Grub Menu first (there is an edit option). If you want to add it permanently (if it works) then you can add it in /boot/grub/menu.lst

---

### Post by baskar007 on 2009-10-10
> **Tony Flury said:**
> There you go - your kernel is not recognising the ACPI capability in your BIOS.

You will need to add "acpi=force" to your kernel start up command - i would try it from the Grub Menu first (there is an edit option). If you want to add it permanently (if it works) then you can add it in /boot/grub/menu.lst
Thankyou,
 Tony Flury . Now my problem was solved.
once again thank you :)

---

