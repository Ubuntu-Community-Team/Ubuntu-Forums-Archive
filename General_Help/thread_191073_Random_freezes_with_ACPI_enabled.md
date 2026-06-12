---
title: "Random freezes with ACPI enabled"
date: 2006-06-07
forum: General Help
---

### Post by dogen2 on 2006-06-07
Hi

I've noticed Dapper freezes randomly on my laptop about once every 18 hours. I can still see everything on the screen, but the keyboard stops responding, the mouse doesn't move, and I end up having to reboot the machine. I read a thread about a similar problem that said it's an ACPI issue, and that removing some kernel modules related to ACPI might help. Here are the acpi-related modules loaded on my system:

toshiba_acpi           11076  0
dev_acpi               11236  0
acpi_sbs               20172  0
battery                 9988  1 acpi_sbs
ac                      5220  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               22848  1 i2c_acpi_ec

I've tried removing some of them but it doesn't seem to help.

When I add the options noacpi and acpi=off to the /boot/grub/menu.lst boot options, my computer stops freezing. But then I don't get any ACPI features. I'm currently using a Toshiba Satellite A45-S151 laptop.

Is there any way to keep ACPI and avoid the freezing? Are there any log files I can check out to debug this? Thanks!

---

### Post by jasin on 2007-01-12
Seems like you're not the only one with acpi problems, the forums here are plagued with posts about acpi problems. There are work arounds for nearly every acpi problem, but their just that, work arounds.

I guess we need to post more of our acpi problems on launchpad.net in hopes the developers at ubuntu will get off their lazy asses and fix acpi.

---

