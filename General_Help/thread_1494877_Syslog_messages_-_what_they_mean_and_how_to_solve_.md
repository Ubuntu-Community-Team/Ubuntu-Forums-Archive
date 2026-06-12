---
title: "Syslog messages - what they mean and how to solve 'em?"
date: 2010-05-27
forum: General Help
---

### Post by HotForLinux on 2010-05-27
....

May 27 16:47:57 hostname kernel: [   28.037721] [drm] Initialized drm 1.1.0 20060810
May 27 16:47:57 hostname kernel: [   28.061157] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
May 27 16:47:57 hostname kernel: [   28.061167] PCI: Setting latency timer of device 0000:00:02.0 to 64
May 27 16:47:57 hostname kernel: [   28.061236] [drm] Initialized i915 1.6.0 20060119 on minor 0
[COLOR=Red]May 27 16:48:36 hostname kernel: [   61.556761] spurious 8259A interrupt: IRQ7.[/COLOR]

.......

May 27 16:57:02 hostname /USR/SBIN/CRON[8149]: (username) CMD (/home/username/cron/ntpdate.sh)
[COLOR=Red]May 27 16:57:02 hostname postfix/sendmail[8152]: fatal: open /etc/postfix/main.cf: No such file or directory
May 27 16:57:02 hostname /USR/SBIN/CRON[8148]: (username) MAIL (mailed 65 bytes of output but got status 0x004b )
May 27 16:57:26 hostname kernel: [   76.633095] ACPI: EC: non-query interrupt received, switching to interrupt mode[/COLOR]

---

