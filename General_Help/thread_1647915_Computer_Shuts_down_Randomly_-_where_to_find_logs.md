---
title: "Computer Shuts down Randomly - where to find logs?"
date: 2010-12-18
forum: General Help
---

### Post by Max_Mackie on 2010-12-18
My computer randomly shuts off sometimes and I'm not sure what causes it. It doesn't always happen when I'm doing the same thing.

I know this is hardly any info, but if someone could let me know where I can go to find logs and such I could post the output and maybe that will help.

Thanks :)

Also, if this means anything, to restart my computer I need to physically turn it off (the I/O switch on my PS) and let the capacitors on my board empty out before starting it up again.

---

### Post by Rubi1200 on 2010-12-18
Hi,
please post the _full_ specifications for the machine in question.

for troubleshooting, try looking at the following logs for error messages:
dmesg
kern.log
syslog

They can be found in either /var/log

or System > Administration > Log File Viewer

---

### Post by Max_Mackie on 2010-12-18
AMD Athlon 64x2 6000+
Ati HD 3450
3.9GB RAM
Ubuntu 10.10

I tried posting the logs but the server overflowed. Should I host them elsewhere?

---

### Post by cgroza on 2010-12-18
Post only the last 20 lines or so from the file. Those logs contain days of activity, no wonder it overflowed.

---

### Post by Max_Mackie on 2010-12-18
dmesg
```
[   18.521836] [drm] ring test succeeded in 1 usecs
[   18.522033] [drm] radeon: ib pool ready.
[   18.522113] [drm] ib test succeeded in 0 usecs
[   18.522116] [drm] Enabling audio support
[   18.522123] failed to evaluate ATIF got AE_BAD_PARAMETER
[   18.522125] radeon 0000:02:00.0: Error during ACPI methods call
[   18.522187] [drm] Default TV standard: PAL
[   18.522189] [drm] Default TV standard: PAL
[   18.522315] [drm] Default TV standard: PAL
[   18.522421] [drm] Radeon Display Connectors
[   18.522423] [drm] Connector 0:
[   18.522424] [drm]   DIN
[   18.522425] [drm]   Encoders:
[   18.522427] [drm]     TV1: INTERNAL_KLDSCP_DAC2
[   18.522428] [drm] Connector 1:
[   18.522429] [drm]   VGA
[   18.522431] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[   18.522433] [drm]   Encoders:
[   18.522434] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   18.522435] [drm] Connector 2:
[   18.522436] [drm]   DVI-I
[   18.522437] [drm]   HPD1
[   18.522439] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[   18.522441] [drm]   Encoders:
[   18.522442] [drm]     CRT2: INTERNAL_KLDSCP_DAC2
[   18.522443] [drm]     DFP1: INTERNAL_KLDSCP_LVTMA
[   18.633709] [drm] Internal thermal controller with fan control
[   18.633734] [drm] radeon: power management initialized
[   18.706438]   alloc irq_desc for 46 on node 0
[   18.706442]   alloc kstat_irqs on node 0
[   18.706452] forcedeth 0000:00:0a.0: irq 46 for MSI/MSI-X
[   18.731112] type=1400 audit(1292657788.435:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1222 comm="apparmor_parser"
[   18.733298] type=1400 audit(1292657788.435:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1223 comm="apparmor_parser"
[   18.733503] type=1400 audit(1292657788.435:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1223 comm="apparmor_parser"
[   18.733620] type=1400 audit(1292657788.435:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1223 comm="apparmor_parser"
[   18.744219] type=1400 audit(1292657788.445:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1227 comm="apparmor_parser"
[   18.746901] type=1400 audit(1292657788.445:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=1227 comm="apparmor_parser"
[   18.749775] type=1400 audit(1292657788.445:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=1227 comm="apparmor_parser"
[   18.828214] [drm] fb mappable at 0xE0141000
[   18.828217] [drm] vram apper at 0xE0000000
[   18.828218] [drm] size 7258112
[   18.828219] [drm] fb depth is 24
[   18.828220] [drm]    pitch is 6912
[   19.075866] Console: switching to colour frame buffer device 210x65
[   19.081574] fb0: radeondrmfb frame buffer device
[   19.081575] drm: registered panic notifier
[   19.081584] Slow work thread pool: Starting up
[   19.081694] Slow work thread pool: Ready
[   19.081700] [drm] Initialized radeon 2.5.0 20080528 for 0000:02:00.0 on minor 0
```

kern.log
```
Dec 18 02:36:28 max-desktop kernel: [   19.081700] [drm] Initialized radeon 2.5.0 20080528 for 0000:02:00.0 on minor 0
Dec 18 02:36:34 max-desktop kernel: [   21.029641] vboxdrv: Trying to deactivate the NMI watchdog permanently...
Dec 18 02:36:34 max-desktop kernel: [   21.029645] vboxdrv: Successfully done.
Dec 18 02:36:34 max-desktop kernel: [   21.029646] vboxdrv: Found 2 processor cores.
Dec 18 02:36:34 max-desktop kernel: [   21.030180] VBoxDrv: dbg - g_abExecMemory=ffffffffa0393d60
Dec 18 02:36:34 max-desktop kernel: [   21.030192] vboxdrv: fAsync=1 offMin=0x6f7db offMax=0x6f7db
Dec 18 02:36:34 max-desktop kernel: [   21.031081] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
Dec 18 02:36:34 max-desktop kernel: [   21.031084] vboxdrv: Successfully loaded version 3.2.10 (interface 0x00140001).
Dec 18 02:36:34 max-desktop kernel: [   21.260942] ACPI: PCI Interrupt Link [AE0B] enabled at IRQ 16
Dec 18 02:36:34 max-desktop kernel: [   21.260948] HDA Intel 0000:02:00.1: PCI INT B -> Link[AE0B] -> GSI 16 (level, low) -> IRQ 16
Dec 18 02:36:34 max-desktop kernel: [   21.261021]   alloc irq_desc for 47 on node 0
Dec 18 02:36:34 max-desktop kernel: [   21.261023]   alloc kstat_irqs on node 0
Dec 18 02:36:34 max-desktop kernel: [   21.261032] HDA Intel 0000:02:00.1: irq 47 for MSI/MSI-X
Dec 18 02:36:34 max-desktop kernel: [   21.261054] HDA Intel 0000:02:00.1: setting latency timer to 64
Dec 18 02:36:35 max-desktop kernel: [   21.493960] ppdev: user-space parallel port driver
Dec 18 02:36:39 max-desktop kernel: [   25.884902] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
Dec 18 02:36:43 max-desktop kernel: [   29.303589] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Dec 18 02:37:00 max-desktop kernel: [   47.093016] lo: Disabled Privacy Extensions
Dec 18 12:45:49 max-desktop kernel: [36576.241298] lo: Disabled Privacy Extensions
```
(this log has A TON of entries for last night. Like a couple hundred entries that happened at the same exact timestamp)

syslog
```
Dec 18 02:42:09 max-desktop anacron[1351]: Job `cron.daily' terminated
Dec 18 02:42:09 max-desktop anacron[1351]: Normal exit (1 job run)
Dec 18 02:42:58 max-desktop NetworkManager[1198]: <info> kernel firmware directory '/lib/firmware' changed
Dec 18 02:43:07 max-desktop dbus-daemon: [system] Reloaded configuration
Dec 18 02:43:43 max-desktop dbus-daemon: last message repeated 4 times
Dec 18 02:43:44 max-desktop AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/f88238fc8c1e4944b86cf93d4a0d6741
Dec 18 02:48:55 max-desktop AptDaemon: INFO: Quiting due to inactivity
Dec 18 02:48:55 max-desktop AptDaemon: INFO: Shutdown was requested
Dec 18 03:17:01 max-desktop CRON[5566]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 18 04:17:01 max-desktop CRON[5581]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 18 05:17:01 max-desktop CRON[5599]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 18 06:17:01 max-desktop CRON[5614]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 18 06:25:01 max-desktop CRON[5618]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))
Dec 18 07:17:01 max-desktop CRON[5632]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 18 07:30:01 max-desktop CRON[5636]: (root) CMD (start -q anacron || :)
Dec 18 07:30:01 max-desktop anacron[5639]: Anacron 2.3 started on 2010-12-18
Dec 18 07:30:01 max-desktop anacron[5639]: Normal exit (0 jobs run)
Dec 18 08:17:01 max-desktop CRON[5653]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 18 09:17:01 max-desktop CRON[5669]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 18 10:17:01 max-desktop CRON[5687]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 18 11:17:01 max-desktop CRON[5701]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 18 12:17:01 max-desktop CRON[5844]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 18 12:45:49 max-desktop kernel: [36576.241298] lo: Disabled Privacy Extensions
```

---

### Post by Max_Mackie on 2010-12-18
bump

---

### Post by amauk on 2010-12-18
Intermittent problems like this are usually a hardware issue.
Either a component is overheating or the power supply is spiking

If you can, try running with the sides of the case removed, and see if that changes anything
Else try to use another power supply

---

### Post by Max_Mackie on 2010-12-18
Its funny you say that because I've gone through 2 power supplies already. What sort of things would make the PS spike? Sometimes my computer is on for days before it shuts off, something for hours.

---

### Post by MooPi on 2010-12-18
It could be many things. The trick is to narrow the options. First thing to check should be your memory. Use the Ubuntu install CD or down load Memtest iso and burn to a CDrom . Boot from the disk and let memtest run through a couple of times. Unless you have the tools to check further, you should probably take your computer to a technician. They should be able to check the other devices, power supply motherboard etc. The outlet your using for your computer should be checked as well if you keep loosing power supply's. It may not be grounded properly.

---

