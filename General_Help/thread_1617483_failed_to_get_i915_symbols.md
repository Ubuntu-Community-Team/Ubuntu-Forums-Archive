---
title: "failed to get i915 symbols"
date: 2010-11-09
forum: General Help
---

### Post by nonabhai on 2010-11-09
Ubuntu 10.10 (Maverick)
Kernel 2.6.35-22

I have recently upgraded from Ubuntu 10.04 to Ubuntu 10.10

Now every time when I boot, I get following error:

```
Intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
```

What may be the solution??? Please help

Thnx

---

### Post by Rubi1200 on 2010-11-09
Hi,
are you still able to boot into Ubuntu despite the message or not at all?

If you can boot into Ubuntu, post the output of the following commands please:

```
lspci | grep VGA

dmesg | grep intel

</var/log/kern.log grep intel
```

Thanks.

---

### Post by drs305 on 2010-11-09
I remember working a recent Grub problem where someone posted a kernel option regarding i915. Could that be the answer?

I'll get the link in a moment.

Added: Here you go. Don't know if it's the solution to your problem or not.
[http://ubuntuforums.org/showthread.php?t=1590847]("http://ubuntuforums.org/showthread.php?t=1590847")

---

### Post by nonabhai on 2010-11-10
> **Rubi1200 said:**
> Hi,
are you still able to boot into Ubuntu despite the message or not at all?

If you can boot into Ubuntu, post the output of the following commands please:

Thanks.
Thanks for reply, yes am still able to boot into Ubuntu
Here is the output:
```

** lspci | grep VGA:**
02:00.0 VGA compatible controller: ATI Technologies Inc M92 LP [Mobility Radeon HD 4300 Series]

** dmesg | grep intel:**
[    0.946835] intel_idle: MWAIT substates: 0x1120
[    0.946836] intel_idle: v0.4 model 0x25
[    0.946837] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.948275] ACPI: acpi_idle yielding to intel_idle
[   11.858277] intel ips 0000:00:1f.6: Warning: CPU TDP doesn't match expected value (found 25, expected 35)
[   11.858317] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   11.858485] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
[   11.988586] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 65535
[   21.814506] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[18446744054.927303] intel ips 0000:00:1f.6: restoring config space at offset 0xf (was 0x300, writing 0x30a)
[18446744054.927325] intel ips 0000:00:1f.6: restoring config space at offset 0x1 (was 0x100000, writing 0x100002)

** </var/log/kern.log grep intel:**
Nov  9 06:04:55 nvd-laptop kernel: [   35.440686] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
Nov  9 13:11:03 nvd-laptop kernel: [    0.929057] intel_idle: MWAIT substates: 0x1120
Nov  9 13:11:03 nvd-laptop kernel: [    0.929059] intel_idle: v0.4 model 0x25
Nov  9 13:11:03 nvd-laptop kernel: [    0.929060] intel_idle: lapic_timer_reliable_states 0xffffffff
Nov  9 13:11:03 nvd-laptop kernel: [    0.931186] ACPI: acpi_idle yielding to intel_idle
Nov  9 13:11:03 nvd-laptop kernel: [   14.057884] intel ips 0000:00:1f.6: Warning: CPU TDP doesn't match expected value (found 25, expected 35)
Nov  9 13:11:03 nvd-laptop kernel: [   14.057919] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Nov  9 13:11:03 nvd-laptop kernel: [   14.058025] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
Nov  9 13:11:03 nvd-laptop kernel: [   14.058241] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 65535
Nov  9 13:11:25 nvd-laptop kernel: [   38.102120] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
Nov  9 13:13:44 nvd-laptop kernel: [    0.929758] intel_idle: MWAIT substates: 0x1120
Nov  9 13:13:44 nvd-laptop kernel: [    0.929759] intel_idle: v0.4 model 0x25
Nov  9 13:13:44 nvd-laptop kernel: [    0.929760] intel_idle: lapic_timer_reliable_states 0xffffffff
Nov  9 13:13:44 nvd-laptop kernel: [    0.931323] ACPI: acpi_idle yielding to intel_idle
Nov  9 13:13:44 nvd-laptop kernel: [   12.430158] intel ips 0000:00:1f.6: Warning: CPU TDP doesn't match expected value (found 25, expected 35)
Nov  9 13:13:44 nvd-laptop kernel: [   12.430196] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Nov  9 13:13:44 nvd-laptop kernel: [   12.430339] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
Nov  9 13:13:44 nvd-laptop kernel: [   12.496627] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 65535
Nov  9 13:13:49 nvd-laptop kernel: [   18.762932] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
Nov  9 13:15:09 nvd-laptop kernel: [    0.942856] intel_idle: MWAIT substates: 0x1120
Nov  9 13:15:09 nvd-laptop kernel: [    0.942858] intel_idle: v0.4 model 0x25
Nov  9 13:15:09 nvd-laptop kernel: [    0.942859] intel_idle: lapic_timer_reliable_states 0xffffffff
Nov  9 13:15:09 nvd-laptop kernel: [    0.945362] ACPI: acpi_idle yielding to intel_idle
Nov  9 13:15:09 nvd-laptop kernel: [   11.974628] intel ips 0000:00:1f.6: Warning: CPU TDP doesn't match expected value (found 25, expected 35)
Nov  9 13:15:09 nvd-laptop kernel: [   11.974665] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Nov  9 13:15:09 nvd-laptop kernel: [   11.974822] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
Nov  9 13:15:09 nvd-laptop kernel: [   12.035738] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 65535
Nov  9 13:18:59 nvd-laptop kernel: [    0.927869] intel_idle: MWAIT substates: 0x1120
Nov  9 13:18:59 nvd-laptop kernel: [    0.927870] intel_idle: v0.4 model 0x25
Nov  9 13:18:59 nvd-laptop kernel: [    0.927872] intel_idle: lapic_timer_reliable_states 0xffffffff
Nov  9 13:18:59 nvd-laptop kernel: [    0.929533] ACPI: acpi_idle yielding to intel_idle
Nov  9 13:18:59 nvd-laptop kernel: [   10.463600] intel ips 0000:00:1f.6: Warning: CPU TDP doesn't match expected value (found 25, expected 35)
Nov  9 13:18:59 nvd-laptop kernel: [   10.463635] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Nov  9 13:18:59 nvd-laptop kernel: [   10.463773] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
Nov  9 13:18:59 nvd-laptop kernel: [   10.463970] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 65535
Nov  9 13:19:20 nvd-laptop kernel: [   34.307746] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
Nov  9 15:23:31 nvd-laptop kernel: [ 7470.288275] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Nov  9 15:23:36 nvd-laptop kernel: [ 7475.277680] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Nov  9 15:25:11 nvd-laptop kernel: [    1.068537] intel_idle: MWAIT substates: 0x1120
Nov  9 15:25:11 nvd-laptop kernel: [    1.068541] intel_idle: v0.4 model 0x25
Nov  9 15:25:11 nvd-laptop kernel: [    1.068543] intel_idle: lapic_timer_reliable_states 0xffffffff
Nov  9 15:25:11 nvd-laptop kernel: [    1.070837] ACPI: acpi_idle yielding to intel_idle
Nov  9 15:25:11 nvd-laptop kernel: [   11.792476] intel ips 0000:00:1f.6: Warning: CPU TDP doesn't match expected value (found 25, expected 35)
Nov  9 15:25:11 nvd-laptop kernel: [   11.792508] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Nov  9 15:25:11 nvd-laptop kernel: [   11.792606] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
Nov  9 15:25:11 nvd-laptop kernel: [   11.792759] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 65535
Nov  9 15:25:23 nvd-laptop kernel: [   38.225562] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
Nov  9 18:49:41 nvd-laptop kernel: [18446744053.159165] intel ips 0000:00:1f.6: restoring config space at offset 0xf (was 0x300, writing 0x30a)
Nov  9 18:49:41 nvd-laptop kernel: [18446744053.159191] intel ips 0000:00:1f.6: restoring config space at offset 0x1 (was 0x100000, writing 0x100002)
Nov  9 19:21:05 nvd-laptop kernel: [    1.324152] intel_idle: MWAIT substates: 0x1120
Nov  9 19:21:05 nvd-laptop kernel: [    1.324154] intel_idle: v0.4 model 0x25
Nov  9 19:21:05 nvd-laptop kernel: [    1.324155] intel_idle: lapic_timer_reliable_states 0xffffffff
Nov  9 19:21:05 nvd-laptop kernel: [    1.325302] ACPI: acpi_idle yielding to intel_idle
Nov  9 19:21:05 nvd-laptop kernel: [   20.305962] intel ips 0000:00:1f.6: CPU TDP doesn't match expected value (found 25, expected 29)
Nov  9 19:21:05 nvd-laptop kernel: [   20.305992] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Nov  9 19:21:05 nvd-laptop kernel: [   20.306094] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
Nov  9 19:21:05 nvd-laptop kernel: [   20.306246] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 90
Nov  9 19:26:47 nvd-laptop kernel: [    1.660574] intel_idle: MWAIT substates: 0x1120
Nov  9 19:26:47 nvd-laptop kernel: [    1.660577] intel_idle: v0.4 model 0x25
Nov  9 19:26:47 nvd-laptop kernel: [    1.660579] intel_idle: lapic_timer_reliable_states 0xffffffff
Nov  9 19:26:47 nvd-laptop kernel: [    1.662305] ACPI: acpi_idle yielding to intel_idle
Nov  9 19:26:47 nvd-laptop kernel: [   20.624864] intel ips 0000:00:1f.6: CPU TDP doesn't match expected value (found 25, expected 29)
Nov  9 19:26:47 nvd-laptop kernel: [   20.624895] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Nov  9 19:26:47 nvd-laptop kernel: [   20.625002] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
Nov  9 19:26:47 nvd-laptop kernel: [   20.625163] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 90
Nov  9 19:29:09 nvd-laptop kernel: [    1.342167] intel_idle: MWAIT substates: 0x1120
Nov  9 19:29:09 nvd-laptop kernel: [    1.342169] intel_idle: v0.4 model 0x25
Nov  9 19:29:09 nvd-laptop kernel: [    1.342170] intel_idle: lapic_timer_reliable_states 0xffffffff
Nov  9 19:29:09 nvd-laptop kernel: [    1.345273] ACPI: acpi_idle yielding to intel_idle
Nov  9 19:29:09 nvd-laptop kernel: [   20.510452] intel ips 0000:00:1f.6: CPU TDP doesn't match expected value (found 25, expected 29)
Nov  9 19:29:09 nvd-laptop kernel: [   20.510480] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Nov  9 19:29:09 nvd-laptop kernel: [   20.510612] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
Nov  9 19:29:09 nvd-laptop kernel: [   20.510781] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 90
Nov  9 19:31:21 nvd-laptop kernel: [    1.324458] intel_idle: MWAIT substates: 0x1120
Nov  9 19:31:21 nvd-laptop kernel: [    1.324459] intel_idle: v0.4 model 0x25
Nov  9 19:31:21 nvd-laptop kernel: [    1.324460] intel_idle: lapic_timer_reliable_states 0xffffffff
Nov  9 19:31:21 nvd-laptop kernel: [    1.326662] ACPI: acpi_idle yielding to intel_idle
Nov  9 19:31:21 nvd-laptop kernel: [   20.088005] intel ips 0000:00:1f.6: CPU TDP doesn't match expected value (found 25, expected 29)
Nov  9 19:31:21 nvd-laptop kernel: [   20.088034] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Nov  9 19:31:21 nvd-laptop kernel: [   20.088168] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
Nov  9 19:31:21 nvd-laptop kernel: [   20.088371] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 90
Nov  9 19:53:50 nvd-laptop kernel: [    1.066213] intel_idle: MWAIT substates: 0x1120
Nov  9 19:53:50 nvd-laptop kernel: [    1.066217] intel_idle: v0.4 model 0x25
Nov  9 19:53:50 nvd-laptop kernel: [    1.066219] intel_idle: lapic_timer_reliable_states 0xffffffff
Nov  9 19:53:50 nvd-laptop kernel: [    1.068575] ACPI: acpi_idle yielding to intel_idle
Nov  9 19:53:50 nvd-laptop kernel: [   19.211130] intel ips 0000:00:1f.6: Warning: CPU TDP doesn't match expected value (found 25, expected 35)
Nov  9 19:53:50 nvd-laptop kernel: [   19.211166] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Nov  9 19:53:50 nvd-laptop kernel: [   19.211302] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
Nov  9 19:53:50 nvd-laptop kernel: [   19.237619] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 65535
Nov  9 19:53:57 nvd-laptop kernel: [   28.076461] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
Nov  9 19:56:03 nvd-laptop kernel: [    1.316427] intel_idle: MWAIT substates: 0x1120
Nov  9 19:56:03 nvd-laptop kernel: [    1.316429] intel_idle: v0.4 model 0x25
Nov  9 19:56:03 nvd-laptop kernel: [    1.316430] intel_idle: lapic_timer_reliable_states 0xffffffff
Nov  9 19:56:03 nvd-laptop kernel: [    1.317701] ACPI: acpi_idle yielding to intel_idle
Nov  9 19:56:03 nvd-laptop kernel: [   20.832225] intel ips 0000:00:1f.6: CPU TDP doesn't match expected value (found 25, expected 29)
Nov  9 19:56:03 nvd-laptop kernel: [   20.832256] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Nov  9 19:56:03 nvd-laptop kernel: [   20.832400] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
Nov  9 19:56:03 nvd-laptop kernel: [   20.832793] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 90
Nov  9 20:00:03 nvd-laptop kernel: [    0.930149] intel_idle: MWAIT substates: 0x1120
Nov  9 20:00:03 nvd-laptop kernel: [    0.930151] intel_idle: v0.4 model 0x25
Nov  9 20:00:03 nvd-laptop kernel: [    0.930152] intel_idle: lapic_timer_reliable_states 0xffffffff
Nov  9 20:00:03 nvd-laptop kernel: [    0.931582] ACPI: acpi_idle yielding to intel_idle
Nov  9 20:00:03 nvd-laptop kernel: [   19.304987] intel ips 0000:00:1f.6: Warning: CPU TDP doesn't match expected value (found 25, expected 35)
Nov  9 20:00:03 nvd-laptop kernel: [   19.305024] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Nov  9 20:00:03 nvd-laptop kernel: [   19.305168] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
Nov  9 20:00:03 nvd-laptop kernel: [   19.361258] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 65535
Nov  9 20:00:11 nvd-laptop kernel: [   28.583390] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
Nov  9 20:43:03 nvd-laptop kernel: [    1.324373] intel_idle: MWAIT substates: 0x1120
Nov  9 20:43:03 nvd-laptop kernel: [    1.324374] intel_idle: v0.4 model 0x25
Nov  9 20:43:03 nvd-laptop kernel: [    1.324375] intel_idle: lapic_timer_reliable_states 0xffffffff
Nov  9 20:43:03 nvd-laptop kernel: [    1.325647] ACPI: acpi_idle yielding to intel_idle
Nov  9 20:43:03 nvd-laptop kernel: [   20.788016] intel ips 0000:00:1f.6: CPU TDP doesn't match expected value (found 25, expected 29)
Nov  9 20:43:03 nvd-laptop kernel: [   20.788047] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Nov  9 20:43:03 nvd-laptop kernel: [   20.788200] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
Nov  9 20:43:03 nvd-laptop kernel: [   20.788357] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 90
Nov  9 20:44:18 nvd-laptop kernel: [    0.928482] intel_idle: MWAIT substates: 0x1120
Nov  9 20:44:18 nvd-laptop kernel: [    0.928484] intel_idle: v0.4 model 0x25
Nov  9 20:44:18 nvd-laptop kernel: [    0.928485] intel_idle: lapic_timer_reliable_states 0xffffffff
Nov  9 20:44:18 nvd-laptop kernel: [    0.930168] ACPI: acpi_idle yielding to intel_idle
Nov  9 20:44:18 nvd-laptop kernel: [   19.052863] intel ips 0000:00:1f.6: Warning: CPU TDP doesn't match expected value (found 25, expected 35)
Nov  9 20:44:18 nvd-laptop kernel: [   19.052904] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Nov  9 20:44:18 nvd-laptop kernel: [   19.053031] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
Nov  9 20:44:18 nvd-laptop kernel: [   19.097301] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 65535
Nov  9 20:44:27 nvd-laptop kernel: [   29.581561] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
Nov  9 21:09:03 nvd-laptop kernel: [    1.351929] intel_idle: MWAIT substates: 0x1120
Nov  9 21:09:03 nvd-laptop kernel: [    1.351931] intel_idle: v0.4 model 0x25
Nov  9 21:09:03 nvd-laptop kernel: [    1.351932] intel_idle: lapic_timer_reliable_states 0xffffffff
Nov  9 21:09:03 nvd-laptop kernel: [    1.353397] ACPI: acpi_idle yielding to intel_idle
Nov  9 21:09:03 nvd-laptop kernel: [   20.453408] intel ips 0000:00:1f.6: CPU TDP doesn't match expected value (found 25, expected 29)
Nov  9 21:09:03 nvd-laptop kernel: [   20.453438] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Nov  9 21:09:03 nvd-laptop kernel: [   20.453575] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
Nov  9 21:09:03 nvd-laptop kernel: [   20.453688] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 90
Nov  9 21:12:59 nvd-laptop kernel: [    0.947512] intel_idle: MWAIT substates: 0x1120
Nov  9 21:12:59 nvd-laptop kernel: [    0.947514] intel_idle: v0.4 model 0x25
Nov  9 21:12:59 nvd-laptop kernel: [    0.947515] intel_idle: lapic_timer_reliable_states 0xffffffff
Nov  9 21:12:59 nvd-laptop kernel: [    0.949024] ACPI: acpi_idle yielding to intel_idle
Nov  9 21:12:59 nvd-laptop kernel: [   19.196876] intel ips 0000:00:1f.6: Warning: CPU TDP doesn't match expected value (found 25, expected 35)
Nov  9 21:12:59 nvd-laptop kernel: [   19.196913] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Nov  9 21:12:59 nvd-laptop kernel: [   19.197054] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
Nov  9 21:12:59 nvd-laptop kernel: [   19.220831] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 65535
Nov  9 21:13:07 nvd-laptop kernel: [   29.026626] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
Nov  9 21:24:13 nvd-laptop kernel: [    1.345546] intel_idle: MWAIT substates: 0x1120
Nov  9 21:24:13 nvd-laptop kernel: [    1.345548] intel_idle: v0.4 model 0x25
Nov  9 21:24:13 nvd-laptop kernel: [    1.345549] intel_idle: lapic_timer_reliable_states 0xffffffff
Nov  9 21:24:13 nvd-laptop kernel: [    1.346698] ACPI: acpi_idle yielding to intel_idle
Nov  9 21:24:13 nvd-laptop kernel: [   20.682497] intel ips 0000:00:1f.6: CPU TDP doesn't match expected value (found 25, expected 29)
Nov  9 21:24:13 nvd-laptop kernel: [   20.693308] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Nov  9 21:24:13 nvd-laptop kernel: [   20.693449] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
Nov  9 21:24:13 nvd-laptop kernel: [   20.718205] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 90
Nov  9 21:25:26 nvd-laptop kernel: [    0.948517] intel_idle: MWAIT substates: 0x1120
Nov  9 21:25:26 nvd-laptop kernel: [    0.948519] intel_idle: v0.4 model 0x25
Nov  9 21:25:26 nvd-laptop kernel: [    0.948520] intel_idle: lapic_timer_reliable_states 0xffffffff
Nov  9 21:25:26 nvd-laptop kernel: [    0.949999] ACPI: acpi_idle yielding to intel_idle
Nov  9 21:25:26 nvd-laptop kernel: [   19.238813] intel ips 0000:00:1f.6: Warning: CPU TDP doesn't match expected value (found 25, expected 35)
Nov  9 21:25:26 nvd-laptop kernel: [   19.238867] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Nov  9 21:25:26 nvd-laptop kernel: [   19.239046] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
Nov  9 21:25:26 nvd-laptop kernel: [   19.347371] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 65535
Nov  9 21:25:33 nvd-laptop kernel: [   28.265294] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
Nov  9 22:47:05 nvd-laptop kernel: [    0.948215] intel_idle: MWAIT substates: 0x1120
Nov  9 22:47:05 nvd-laptop kernel: [    0.948217] intel_idle: v0.4 model 0x25
Nov  9 22:47:05 nvd-laptop kernel: [    0.948218] intel_idle: lapic_timer_reliable_states 0xffffffff
Nov  9 22:47:05 nvd-laptop kernel: [    0.949796] ACPI: acpi_idle yielding to intel_idle
Nov  9 22:47:05 nvd-laptop kernel: [    9.856372] intel ips 0000:00:1f.6: Warning: CPU TDP doesn't match expected value (found 25, expected 35)
Nov  9 22:47:05 nvd-laptop kernel: [    9.856410] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Nov  9 22:47:05 nvd-laptop kernel: [    9.856557] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
Nov  9 22:47:05 nvd-laptop kernel: [    9.857044] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 65535
Nov  9 22:47:29 nvd-laptop kernel: [   36.704954] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
Nov 10 06:28:00 nvd-laptop kernel: [    0.948315] intel_idle: MWAIT substates: 0x1120
Nov 10 06:28:00 nvd-laptop kernel: [    0.948317] intel_idle: v0.4 model 0x25
Nov 10 06:28:00 nvd-laptop kernel: [    0.948318] intel_idle: lapic_timer_reliable_states 0xffffffff
Nov 10 06:28:00 nvd-laptop kernel: [    0.950029] ACPI: acpi_idle yielding to intel_idle
Nov 10 06:28:00 nvd-laptop kernel: [   11.901360] intel ips 0000:00:1f.6: Warning: CPU TDP doesn't match expected value (found 25, expected 35)
Nov 10 06:28:00 nvd-laptop kernel: [   11.901401] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Nov 10 06:28:00 nvd-laptop kernel: [   11.901574] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
Nov 10 06:28:00 nvd-laptop kernel: [   11.979324] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 65535
Nov 10 06:28:07 nvd-laptop kernel: [   20.459166] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
Nov 10 07:12:39 nvd-laptop kernel: [ 2686.476343] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Nov 10 07:12:59 nvd-laptop kernel: [ 2706.434489] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Nov 10 07:13:04 nvd-laptop kernel: [ 2711.424500] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Nov 10 07:21:04 nvd-laptop kernel: [ 3190.545620] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Nov 10 07:21:09 nvd-laptop kernel: [ 3195.535438] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Nov 10 07:21:14 nvd-laptop kernel: [ 3200.532744] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Nov 10 07:21:19 nvd-laptop kernel: [ 3205.522623] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Nov 10 07:21:24 nvd-laptop kernel: [ 3210.505492] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Nov 10 07:21:29 nvd-laptop kernel: [ 3215.502201] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Nov 10 07:21:34 nvd-laptop kernel: [ 3220.482063] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Nov 10 07:21:39 nvd-laptop kernel: [ 3225.471900] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Nov 10 07:21:44 nvd-laptop kernel: [ 3230.471066] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Nov 10 07:21:54 nvd-laptop kernel: [ 3240.443802] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Nov 10 07:21:59 nvd-laptop kernel: [ 3245.439660] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Nov 10 07:22:04 nvd-laptop kernel: [ 3250.420919] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Nov 10 07:22:09 nvd-laptop kernel: [ 3255.413289] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Nov 10 07:22:14 nvd-laptop kernel: [ 3260.403078] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Nov 10 07:22:19 nvd-laptop kernel: [ 3265.400392] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Nov 10 07:22:24 nvd-laptop kernel: [ 3270.388710] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Nov 10 07:24:49 nvd-laptop kernel: [    1.096657] intel_idle: MWAIT substates: 0x1120
Nov 10 07:24:49 nvd-laptop kernel: [    1.096660] intel_idle: v0.4 model 0x25
Nov 10 07:24:49 nvd-laptop kernel: [    1.096663] intel_idle: lapic_timer_reliable_states 0xffffffff
Nov 10 07:24:49 nvd-laptop kernel: [    1.099092] ACPI: acpi_idle yielding to intel_idle
Nov 10 07:24:49 nvd-laptop kernel: [   12.194341] intel ips 0000:00:1f.6: Warning: CPU TDP doesn't match expected value (found 25, expected 35)
Nov 10 07:24:49 nvd-laptop kernel: [   12.194381] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Nov 10 07:24:49 nvd-laptop kernel: [   12.194532] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
Nov 10 07:24:49 nvd-laptop kernel: [   12.311734] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 65535
Nov 10 07:24:56 nvd-laptop kernel: [   20.605067] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
Nov 10 08:41:13 nvd-laptop kernel: [18446744054.020977] intel ips 0000:00:1f.6: restoring config space at offset 0xf (was 0x300, writing 0x30a)
Nov 10 08:41:13 nvd-laptop kernel: [18446744054.021005] intel ips 0000:00:1f.6: restoring config space at offset 0x1 (was 0x100000, writing 0x100002)
Nov 10 10:27:23 nvd-laptop kernel: [    0.948216] intel_idle: MWAIT substates: 0x1120
Nov 10 10:27:23 nvd-laptop kernel: [    0.948218] intel_idle: v0.4 model 0x25
Nov 10 10:27:23 nvd-laptop kernel: [    0.948219] intel_idle: lapic_timer_reliable_states 0xffffffff
Nov 10 10:27:23 nvd-laptop kernel: [    0.949689] ACPI: acpi_idle yielding to intel_idle
Nov 10 10:27:23 nvd-laptop kernel: [   12.157169] intel ips 0000:00:1f.6: Warning: CPU TDP doesn't match expected value (found 25, expected 35)
Nov 10 10:27:23 nvd-laptop kernel: [   12.157208] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Nov 10 10:27:23 nvd-laptop kernel: [   12.157356] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
Nov 10 10:27:23 nvd-laptop kernel: [   12.205059] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 65535
Nov 10 10:27:30 nvd-laptop kernel: [   19.968449] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
Nov 10 19:14:25 nvd-laptop kernel: [    0.946835] intel_idle: MWAIT substates: 0x1120
Nov 10 19:14:25 nvd-laptop kernel: [    0.946836] intel_idle: v0.4 model 0x25
Nov 10 19:14:25 nvd-laptop kernel: [    0.946837] intel_idle: lapic_timer_reliable_states 0xffffffff
Nov 10 19:14:25 nvd-laptop kernel: [    0.948275] ACPI: acpi_idle yielding to intel_idle
Nov 10 19:14:25 nvd-laptop kernel: [   11.858277] intel ips 0000:00:1f.6: Warning: CPU TDP doesn't match expected value (found 25, expected 35)
Nov 10 19:14:25 nvd-laptop kernel: [   11.858317] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Nov 10 19:14:25 nvd-laptop kernel: [   11.858485] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
Nov 10 19:14:25 nvd-laptop kernel: [   11.988586] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 65535
Nov 10 19:14:34 nvd-laptop kernel: [   21.814506] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
Nov 10 19:53:26 nvd-laptop kernel: [18446744054.927303] intel ips 0000:00:1f.6: restoring config space at offset 0xf (was 0x300, writing 0x30a)
Nov 10 19:53:26 nvd-laptop kernel: [18446744054.927325] intel ips 0000:00:1f.6: restoring config space at offset 0x1 (was 0x100000, writing 0x100002)
```

---

### Post by Rubi1200 on 2010-11-10
I know it says you have an  [FONT=monospace][/FONT]ATI Radeon card, but did/do you also have onboard integrated Intel graphics?

If you boot with the nolapic parameter does the error message still appear?

When the computer boots and you get to the GRUB menu press "e" to edit the Ubuntu kernel and then using the arrows navigate to the line that ends with > quiet splash
Remove quiet splash and type nolapic then "Ctrl" + "x" to boot.

Report any errors please.

---

### Post by Darkhorse85 on 2010-11-13
Hi, have the same problem on a acer aspire 4741 laptop. When the laptop boots i get the same error message, but my onboard graphics works after boot even though I get this message. 

Intel core i3

---

### Post by Darkhorse85 on 2010-11-13
> **Rubi1200 said:**
> I know it says you have an  [FONT=monospace][/FONT]ATI Radeon card, but did/do you also have onboard integrated Intel graphics?

If you boot with the nolapic parameter does the error message still appear?

When the computer boots and you get to the GRUB menu press "e" to edit the Ubuntu kernel and then using the arrows navigate to the line that ends with 
Remove quiet splash and type nolapic then "Ctrl" + "x" to boot.

Report any errors please.

I tried the above approach and got the same error mesage. In other words it had no visible effect. Here is another thread with lots of people with the same problem. 
[http://www.ge.ubuntuforums.org/showthread.php?t=1594981](http://www.ge.ubuntuforums.org/showthread.php?t=1594981)

---

### Post by nonabhai on 2010-11-21
> **Darkhorse85 said:**
> I tried the above approach and got the same error mesage. In other words it had no visible effect. Here is another thread with lots of people with the same problem. 
[http://www.ge.ubuntuforums.org/showthread.php?t=1594981](http://www.ge.ubuntuforums.org/showthread.php?t=1594981)

Thanx. I have joined that :D

---

### Post by loudog23 on 2011-09-30
Hi Guys,
First time i got stuck on this, i re-installed from scratch..
See signature for machine description

Second time, a week after installation, it crashed again but all my devellopement tools were alredy installed and everything so i tried a few things and here what worked for me.

THe result seems very heiratic (randow :P) but here the procedure i've done..I'm gaming once i a while so i have a win7 partition:
1. rebooted in win7, 
2. ran a dxdiag (dunno if this as anything to do but i was trying to kick on the graphics turbo in anyway)
3. restarted the machine (not shutdown + power-on)
4. after the grub menu i filled my keyboard buffer with CTRL-C and Ctrl-Z alternatively
5. Boom i was in ubuntu again :)

6. i did this -> > [http://linux-software-news-tutorials.blogspot.com/2011/02/fix-bug-failed-to-get-i915-symbols-boot.html](http://linux-software-news-tutorials.blogspot.com/2011/02/fix-bug-failed-to-get-i915-symbols-boot.html)

6.1 edit the blacklist conf file
```
sudo gedit /etc/modprobe.d/blacklist.conf
```
6.2Add this to the end of the file, save and restart:
```
 blacklist intel_ips
```

 :KS 7. rebooted and voila!


:confused: My question is: Does that procedure will redure graphics performance? my 1st guess would be yes but i NEED my linux so i can live with the fall back for now. 


hope this helps someone!
cheers everyone!

---

### Post by ksd5 on 2011-11-09
[https://wiki.archlinux.org/index.php/Intel#KMS_.28Kernel_Mode_Setting.29](https://wiki.archlinux.org/index.php/Intel#KMS_.28Kernel_Mode_Setting.29)

That has some good information on the i915 driver.

---

