---
title: "Reset BIOS causing GRUB/boot errors?"
date: 2011-08-03
forum: General Help
---

### Post by Turpinator. on 2011-08-03
yAlright, so to first understand my problem you must understand what happened to cause my problem.
My problem, GRUB loader appears when it normally did not and Ubuntu fails to boot.
My story, I installed ubuntu on a HP Touchsmart laptop a month ago because I was having troubles with Windows and... well I just wanted to install ubuntu.  All goes well until a week ago when my sound was permanently muted through a hardware switch and ubuntu was not detecting it. I tried hitting the button on my laptop but nothing worked. Soo... I tried resetting my BIOS in hopes that it would fix it. I set the bios to its defaults and booted.  This is where it got weird. the GRUB loader appeared when it normally did not and upon booting, a black screen with flashing cursor would show up and then... nothing. I changed the bios settings back to what they were and still nothing.

I have removed the silent boot from the GRUB boot line and can see whats going on... a little, the last thing it shows is "Running /scripts/init-bottom ... done." annnd nothing else.
When booting in recovery mode it stops after 30 or so seconds on...
```
ACPI: Power Button [PWRB]
input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/inp
```
and just ends on that line.
the previous line shows closing the Lid as a button.

I have tried booting into a live USB (as the laptop has no cd drive) and everything works fine.

If anyone has any sort of input as to how the BIOS would be related to GRUB/booting... help. Please.

---

### Post by dcstar on 2011-08-03
> **Turpinator. said:**
> 
.........
If anyone has any sort of input as to how the BIOS would be related to GRUB/booting... help. Please.

Many things can cause issues in the BIOS, the SATA mode for disk access (IDE, AHCI, RAID etc.) for one.

---

### Post by Turpinator. on 2011-08-03
My bios has about 5 things that can be changed and I changed them all back to their previous settings.

---

