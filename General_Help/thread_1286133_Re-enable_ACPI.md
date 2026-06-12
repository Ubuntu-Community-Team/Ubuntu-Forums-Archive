---
title: "Re-enable ACPI"
date: 2009-10-08
forum: General Help
---

### Post by ejectHD on 2009-10-08
I had to turn off ACPI to properly install Ubuntu on my Dell D630. I want to turn it back on but don't remember how I turned it off. I think I edited the /boot/grub/menu.lst file.

I think I added "acpi=off" and "noapic" to this line:

kernel /boot/vmlinuz-2.6.18-3-amd64 root=/dev/sda1 ro acpi=off noapic

Should I delete "acpi=off" and "noapic" or should I change them to "acpi=on" and "apic"?

Rock On :guitar:

---

### Post by Iowan on 2009-10-08
I'd delete them... but can't give a good reason why.

---

