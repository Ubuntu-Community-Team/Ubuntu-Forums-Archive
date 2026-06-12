---
title: "Lucid: Nautilus struggling with large directories"
date: 2010-05-26
forum: General Help
---

### Post by Robbyx on 2010-05-26
Until Lucid I used pcman. Since lucid it does not open all folders, so I have given up on it.

Nautilus freezes for a long time when opening large folders in particular Bin and Lib (2601). Is there a way of increasing Nautilus' cache so that it does not grab most of the memory when it is opening the very large folders?

---

### Post by dino99 on 2010-05-26
seem to be a problem known for age now :(

---

### Post by Robbyx on 2010-05-26
Is there a solution to allowing other file managers to open subdirectories? In the past when Nautilus played up I would switch to another filemanager. Now I can not do this. So I am stuck. I am surprised that the other filemanagers will not open the subfolders, as prior to lucid this was not a problem.

---

### Post by jordilin on 2010-05-26
In my case /usr/bin and /usr/lib takes indeed a while, but it does not get unresponsive (freeze) and I'm using a 4 year old laptop. You can check /var/log/messages for any possible problem. It could be a hard disk problem as well.

---

### Post by dino99 on 2010-05-26
launchpad is fullfilled with such complaints

---

### Post by Robbyx on 2010-05-26
Can you see anything wrong in the following tail from messages?


```
May 26 09:20:36 localhost squid[1592]: Squid Parent: child process 1598 started
May 26 09:20:36 localhost kernel: [  124.534703] type=1505 audit(1274862036.077:3):  operation="profile_load" pid=1629 name="/usr/share/gdm/guest-session/Xsession"
May 26 09:20:36 localhost kernel: [  124.535839] type=1505 audit(1274862036.077:4):  operation="profile_load" pid=1630 name="/sbin/dhclient3"
May 26 09:20:36 localhost kernel: [  124.536461] type=1505 audit(1274862036.081:5):  operation="profile_load" pid=1630 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
May 26 09:20:36 localhost kernel: [  124.536732] type=1505 audit(1274862036.081:6):  operation="profile_load" pid=1630 name="/usr/lib/connman/scripts/dhclient-script"
May 26 09:20:36 localhost kernel: [  124.538993] type=1505 audit(1274862036.081:7):  operation="profile_load" pid=1631 name="/usr/bin/evince"
May 26 09:20:36 localhost kernel: [  124.545533] type=1505 audit(1274862036.089:8):  operation="profile_load" pid=1631 name="/usr/bin/evince-previewer"
May 26 09:20:36 localhost kernel: [  124.549527] type=1505 audit(1274862036.093:9):  operation="profile_load" pid=1631 name="/usr/bin/evince-thumbnailer"
May 26 09:20:36 localhost kernel: [  124.555563] type=1505 audit(1274862036.097:10):  operation="profile_load" pid=1634 name="/usr/lib/cups/backend/cups-pdf"
May 26 09:20:36 localhost kernel: [  124.556200] type=1505 audit(1274862036.101:11):  operation="profile_load" pid=1634 name="/usr/sbin/cupsd"
May 26 09:20:36 localhost kernel: [  124.804998] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
May 26 09:20:36 localhost kernel: [  124.805001] apm: disabled - APM is not SMP safe.
May 26 09:20:38 localhost prelude-lml: WARNING: prelude-client: error starting prelude-client: profile 'prelude-lml' does not exist#012#012Profile 'prelude-lml' does not exist. In order to create it, please run:#012prelude-admin register "prelude-lml" "idmef:w" <manager address> --uid 0 --gid 0.
May 26 09:20:38 localhost kernel: [  127.429049] 3w-xxxx: scsi5: Unknown scsi opcode: 0x85
May 26 09:20:38 localhost kernel: [  127.429064] 3w-xxxx: scsi5: Unknown scsi opcode: 0x85
May 26 09:20:40 localhost kernel: [  129.230409] vboxdrv: fAsync=0 offMin=0x190 offMax=0x6b0
May 26 09:20:40 localhost kernel: [  129.230660] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
May 26 09:21:47 localhost nautilus: [N-A] Nautilus-Actions Menu Extender 2.30.2 initializing...
May 26 09:21:48 localhost nautilus: [N-A] Nautilus-Actions Tracker 2.30.2 initializing...
May 26 09:44:35 localhost sudo: pam_sm_authenticate: Called
May 26 09:44:35 localhost sudo: pam_sm_authenticate: username = [rob]
May 26 09:44:55 localhost rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="1580" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
May 26 11:09:33 localhost gnome-screensaver-dialog: pam_sm_authenticate: Called
May 26 11:09:33 localhost gnome-screensaver-dialog: pam_sm_authenticate: username = [rob]
May 26 11:58:13 localhost gnome-screensaver-dialog: pam_sm_authenticate: Called
May 26 11:58:13 localhost gnome-screensaver-dialog: pam_sm_authenticate: username = [rob]
May 26 12:00:01 localhost UBUNTUZILLA: /bin/sh: /usr/local/bin/ubuntuzilla.py: not found
May 26 12:52:16 localhost gnome-screensaver-dialog: pam_sm_authenticate: Called
May 26 12:52:16 localhost gnome-screensaver-dialog: pam_sm_authenticate: username = [rob]
May 26 13:14:56 localhost nautilus: [N-A] Nautilus-Actions Menu Extender 2.30.2 initializing...
May 26 13:14:57 localhost nautilus: [N-A] Nautilus-Actions Tracker 2.30.2 initializing...
May 26 13:31:50 localhost gnome-screensaver-dialog: pam_sm_authenticate: Called
May 26 13:31:50 localhost gnome-screensaver-dialog: pam_sm_authenticate: username = [rob]
May 26 13:36:38 localhost sudo: pam_sm_authenticate: Called
May 26 13:36:38 localhost sudo: pam_sm_authenticate: username = [rob]
May 26 13:43:41 localhost nautilus: [N-A] Nautilus-Actions Menu Extender 2.30.2 initializing...
May 26 13:43:41 localhost nautilus: [N-A] Nautilus-Actions Tracker 2.30.2 initializing...
May 26 13:56:42 localhost nautilus: [N-A] Nautilus-Actions Menu Extender 2.30.2 initializing...
May 26 13:56:42 localhost nautilus: [N-A] Nautilus-Actions Tracker 2.30.2 initializing...
May 26 14:16:08 localhost gnome-screensaver-dialog: pam_sm_authenticate: Called
May 26 14:16:08 localhost gnome-screensaver-dialog: pam_sm_authenticate: username = [rob]
```

---

### Post by philinux on 2010-05-26
Maybe this build is better, I might try it out.

[http://www.omgubuntu.co.uk/2010/01/nautilus-simple-install-ppa-streamlined.html](http://www.omgubuntu.co.uk/2010/01/nautilus-simple-install-ppa-streamlined.html)

---

### Post by philinux on 2010-05-26
Cosmetic only, loading /usr/lib still takes 7 seconds.

---

### Post by Robbyx on 2010-05-26
> **philinux said:**
> Cosmetic only, loading /usr/lib still takes 7 seconds.

It took my dual core 2m22s to open the directory and even then I could not scroll down until I waited much longer. I wonder if there is a cache setting that needs adjusting.

---

### Post by philinux on 2010-05-26
> **Robbyx said:**
> It took my dual core 2m22s to open the directory and even then I could not scroll down until I waited much longer. I wonder if there is a cache setting that needs adjusting.

Wow thats a long time. Have a look in /var/log/messages see if any clues. Repeat by starting nautilus in a terminal and see if any errors.

---

### Post by clhsharky on 2010-05-26
Loading /usr/lib takes 4 seconds with 4 year old desktop, here. I cant remember having a problem with nautilus on a desktop. Might be a laptop issue, maybe hd(speed or longevity). With the more demanding APPs and growing OS, its no wonder 7200-hd and SSDs are getting more popular for laptops.

> It took my dual core 2m22s to open the directory
Something is defiantly messed up.

What philinux said.

sharky

---

### Post by Robbyx on 2010-05-26
> **philinux said:**
> Wow thats a long time. Have a look in /var/log/messages see if any clues. Repeat by starting nautilus in a terminal and see if any errors.

Here is the recent log messages. I don't see anything I can react to:

```
May 26 19:14:40 localhost kernel: [29617.544012] sd 4:0:1:0: [sdb] Synchronizing SCSI cache
May 26 19:14:40 localhost kernel: [29617.544224] sd 4:0:1:0: [sdb] Stopping disk
May 26 19:14:40 localhost kernel: [29618.123251] PM: suspend of drv:sd dev:4:0:1:0 complete after 579.238 msecs
May 26 19:14:40 localhost kernel: [29618.123266] sd 3:0:0:0: [sda] Synchronizing SCSI cache
May 26 19:14:40 localhost kernel: [29618.123704] sd 3:0:0:0: [sda] Stopping disk
May 26 19:14:40 localhost kernel: [29618.542396] PM: suspend of drv:sd dev:3:0:0:0 complete after 419.130 msecs
May 26 19:14:40 localhost kernel: [29619.080007] PM: suspend of drv:atkbd dev:serio0 complete after 523.986 msecs
May 26 19:14:40 localhost kernel: [29619.080310] parport_pc 00:09: disabled
May 26 19:14:40 localhost kernel: [29619.080427] serial 00:08: disabled
May 26 19:14:40 localhost kernel: [29619.080442] 3w-xxxx 0000:05:00.0: PCI INT A disabled
May 26 19:14:40 localhost kernel: [29619.080543] pata_jmicron 0000:03:00.0: PCI INT A disabled
May 26 19:14:40 localhost kernel: [29619.423351] PM: suspend of drv:nvidia dev:0000:01:00.0 complete after 327.347 msecs
May 26 19:14:40 localhost kernel: [29619.423420] ata_piix 0000:00:1f.5: PCI INT B disabled
May 26 19:14:40 localhost kernel: [29619.436086] ata_piix 0000:00:1f.2: PCI INT B disabled
May 26 19:14:40 localhost kernel: [29619.452013] ehci_hcd 0000:00:1d.7: PCI INT A disabled
May 26 19:14:40 localhost kernel: [29619.452019] uhci_hcd 0000:00:1d.2: PCI INT C disabled
May 26 19:14:40 localhost kernel: [29619.452025] uhci_hcd 0000:00:1d.1: PCI INT B disabled
May 26 19:14:40 localhost kernel: [29619.452031] uhci_hcd 0000:00:1d.0: PCI INT A disabled
May 26 19:14:40 localhost kernel: [29619.556072] HDA Intel 0000:00:1b.0: PCI INT A disabled
May 26 19:14:40 localhost kernel: [29619.572008] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 119.969 msecs
May 26 19:14:40 localhost kernel: [29619.572014] ehci_hcd 0000:00:1a.7: PCI INT C disabled
May 26 19:14:40 localhost kernel: [29619.572020] uhci_hcd 0000:00:1a.2: PCI INT C disabled
May 26 19:14:40 localhost kernel: [29619.572025] uhci_hcd 0000:00:1a.1: PCI INT B disabled
May 26 19:14:40 localhost kernel: [29619.572031] uhci_hcd 0000:00:1a.0: PCI INT A disabled
May 26 19:14:40 localhost kernel: [29619.572074] PM: suspend of devices complete after 2161.863 msecs
May 26 19:14:40 localhost kernel: [29619.572076] PM: suspend devices took 2.164 seconds
May 26 19:14:40 localhost kernel: [29619.572237] r8169 0000:04:00.0: PME# enabled
May 26 19:14:40 localhost kernel: [29619.620115] PM: late suspend of devices complete after 48.036 msecs
May 26 19:14:40 localhost kernel: [29619.620932] ACPI: Preparing to enter system sleep state S3
May 26 19:14:40 localhost kernel: [29619.636006] Disabling non-boot CPUs ...
May 26 19:14:40 localhost kernel: [29619.804015] CPU 1 is now offline
May 26 19:14:40 localhost kernel: [29619.804018] SMP alternatives: switching to UP code
May 26 19:14:40 localhost kernel: [29619.808937] CPU0: Thermal monitoring enabled (TM2)
May 26 19:14:40 localhost kernel: [29619.808937] Enabling non-boot CPUs ...
May 26 19:14:40 localhost kernel: [29619.808937] SMP alternatives: switching to SMP code
May 26 19:14:40 localhost kernel: [29619.813593] Booting processor 1 APIC 0x1 ip 0x6000
May 26 19:14:40 localhost kernel: [29619.808667] Initializing CPU#1
May 26 19:14:40 localhost kernel: [29619.808667] CPU: L1 I cache: 32K, L1 D cache: 32K
May 26 19:14:40 localhost kernel: [29619.808667] CPU: L2 cache: 6144K
May 26 19:14:40 localhost kernel: [29619.808667] CPU: Physical Processor ID: 0
May 26 19:14:40 localhost kernel: [29619.808667] CPU: Processor Core ID: 1
May 26 19:14:40 localhost kernel: [29619.808667] CPU1: Thermal monitoring enabled (TM2)
May 26 19:14:40 localhost kernel: [29619.904117] CPU1: Intel(R) Core(TM)2 Duo CPU     E8200  @ 2.66GHz stepping 06
May 26 19:14:40 localhost kernel: [29619.904125] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
May 26 19:14:40 localhost kernel: [29619.952401] CPU1 is up
May 26 19:14:40 localhost kernel: [29619.953171] ACPI: Waking up from system sleep state S3
May 26 19:14:40 localhost kernel: [29619.955193] PM: early resume of devices complete after 0.879 msecs
May 26 19:14:40 localhost kernel: [29619.955259] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
May 26 19:14:40 localhost kernel: [29619.955281] usb usb3: root hub lost power or was reset
May 26 19:14:40 localhost kernel: [29619.955295] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
May 26 19:14:40 localhost kernel: [29619.955316] usb usb4: root hub lost power or was reset
May 26 19:14:40 localhost kernel: [29619.955338] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
May 26 19:14:40 localhost kernel: [29619.955359] usb usb5: root hub lost power or was reset
May 26 19:14:40 localhost kernel: [29619.955379] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
May 26 19:14:40 localhost kernel: [29619.955390] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
May 26 19:14:40 localhost kernel: [29620.049334] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
May 26 19:14:40 localhost kernel: [29620.049355] usb usb6: root hub lost power or was reset
May 26 19:14:40 localhost kernel: [29620.049370] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
May 26 19:14:40 localhost kernel: [29620.049391] usb usb7: root hub lost power or was reset
May 26 19:14:40 localhost kernel: [29620.049406] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
May 26 19:14:40 localhost kernel: [29620.049429] usb usb8: root hub lost power or was reset
May 26 19:14:40 localhost kernel: [29620.049444] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
May 26 19:14:40 localhost kernel: [29620.049464] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
May 26 19:14:40 localhost kernel: [29620.050164] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
May 26 19:14:40 localhost kernel: [29620.416646] PM: resume of drv:nvidia dev:0000:01:00.0 complete after 365.666 msecs
May 26 19:14:40 localhost kernel: [29620.416750] pata_jmicron 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
May 26 19:14:40 localhost kernel: [29620.417257] r8169 0000:04:00.0: PME# disabled
May 26 19:14:40 localhost kernel: [29620.417268] 3w-xxxx 0000:05:00.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
May 26 19:14:40 localhost kernel: [29620.417809] serial 00:08: activated
May 26 19:14:40 localhost kernel: [29620.418312] parport_pc 00:09: activated
May 26 19:14:40 localhost kernel: [29620.432028] r8169: eth0: link up
May 26 19:14:40 localhost kernel: [29620.534620] ata1: SATA link down (SStatus 4 SControl 300)
May 26 19:14:40 localhost kernel: [29620.545200] ata3: SATA link down (SStatus 4 SControl 300)
May 26 19:14:40 localhost kernel: [29620.545254] ata2: SATA link down (SStatus 4 SControl 300)
May 26 19:14:40 localhost kernel: [29620.752009] PM: resume of drv:usb dev:usb4 complete after 255.984 msecs
May 26 19:14:40 localhost kernel: [29621.000012] PM: resume of drv:usb dev:usb5 complete after 247.996 msecs
May 26 19:14:40 localhost kernel: [29621.056940] sd 3:0:0:0: [sda] Starting disk
May 26 19:14:40 localhost kernel: [29624.528502] ata5.01: ACPI cmd ef/03:0c:00:00:00:b0 (SET FEATURES) filtered out
May 26 19:14:40 localhost kernel: [29624.528505] ata5.01: ACPI cmd ef/03:46:00:00:00:b0 (SET FEATURES) filtered out
May 26 19:14:40 localhost kernel: [29624.536545] ata5.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
May 26 19:14:40 localhost kernel: [29624.536548] ata5.00: ACPI cmd ef/03:46:00:00:00:a0 (SET FEATURES) filtered out
May 26 19:14:40 localhost kernel: [29624.552568] ata5.00: configured for UDMA/66
May 26 19:14:40 localhost kernel: [29624.576926] ata5.01: configured for UDMA/66
May 26 19:14:40 localhost kernel: [29625.728008] ata4: link is slow to respond, please be patient (ready=0)
May 26 19:14:40 localhost kernel: [29627.520043] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
May 26 19:14:40 localhost kernel: [29627.544189] ata4.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
May 26 19:14:40 localhost kernel: [29627.544192] ata4.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
May 26 19:14:40 localhost kernel: [29627.544194] ata4.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
May 26 19:14:40 localhost kernel: [29627.560309] ata4.00: configured for UDMA/133
May 26 19:14:40 localhost kernel: [29627.564271] PM: resume of drv:sd dev:3:0:0:0 complete after 6507.331 msecs
May 26 19:14:40 localhost kernel: [29630.564004] 
May 26 19:14:40 localhost kernel: [29630.564007] floppy driver state
May 26 19:14:40 localhost kernel: [29630.564008] -------------------
May 26 19:14:40 localhost kernel: [29630.564011] now=7332641 last interrupt=3832623 diff=3500018 last called handler=f8093660
May 26 19:14:40 localhost kernel: [29630.564013] timeout_message=lock fdc
May 26 19:14:40 localhost kernel: [29630.564014] last output bytes:
May 26 19:14:40 localhost kernel: [29630.564016]  1 90 3832379
May 26 19:14:40 localhost kernel: [29630.564018]  0 90 3832379
May 26 19:14:40 localhost kernel: [29630.564019]  1 90 3832379
May 26 19:14:40 localhost kernel: [29630.564020]  2 90 3832379
May 26 19:14:40 localhost kernel: [29630.564022] 12 90 3832379
May 26 19:14:40 localhost kernel: [29630.564023] 1b 90 3832379
May 26 19:14:40 localhost kernel: [29630.564025] ff 90 3832379
May 26 19:14:40 localhost kernel: [29630.564026]  f 80 3832523
May 26 19:14:40 localhost kernel: [29630.564027]  0 90 3832523
May 26 19:14:40 localhost kernel: [29630.564028]  0 91 3832523
May 26 19:14:40 localhost kernel: [29630.564030]  8 81 3832524
May 26 19:14:40 localhost kernel: [29630.564031] e6 80 3832529
May 26 19:14:40 localhost kernel: [29630.564033]  0 90 3832529
May 26 19:14:40 localhost kernel: [29630.564034]  0 90 3832529
May 26 19:14:40 localhost kernel: [29630.564035]  0 90 3832529
May 26 19:14:40 localhost kernel: [29630.564036]  9 90 3832529
May 26 19:14:40 localhost kernel: [29630.564038]  2 90 3832529
May 26 19:14:40 localhost kernel: [29630.564039] 12 90 3832529
May 26 19:14:40 localhost kernel: [29630.564041] 1b 90 3832529
May 26 19:14:40 localhost kernel: [29630.564042] ff 90 3832529
May 26 19:14:40 localhost kernel: [29630.564043] last result at 3832623
May 26 19:14:40 localhost kernel: [29630.564045] last redo_fd_request at 5013824
May 26 19:14:40 localhost kernel: [29630.564046] 
May 26 19:14:40 localhost kernel: [29630.564052] status=0
May 26 19:14:40 localhost kernel: [29630.564053] fdc_busy=1
May 26 19:14:40 localhost kernel: [29630.564054] do_floppy=f80955b0
May 26 19:14:40 localhost kernel: [29630.564055] cont=f809c290
May 26 19:14:40 localhost kernel: [29630.564057] current_req=(null)
May 26 19:14:40 localhost kernel: [29630.564058] command_status=-1
May 26 19:14:40 localhost kernel: [29630.564059] 
May 26 19:14:40 localhost kernel: [29630.564063] floppy0: floppy timeout called
May 26 19:14:40 localhost kernel: [29630.564080] PM: resume of drv:floppy dev:floppy.0 complete after 2999.794 msecs
May 26 19:14:40 localhost kernel: [29630.564092] sd 4:0:1:0: [sdb] Starting disk
May 26 19:14:40 localhost kernel: [29630.844011] usb 4-2: reset low speed USB device using uhci_hcd and address 2
May 26 19:14:40 localhost kernel: [29631.217049] PM: resume of drv:usb dev:4-2 complete after 632.120 msecs
May 26 19:14:40 localhost kernel: [29631.328011] usb 5-1: reset full speed USB device using uhci_hcd and address 2
May 26 19:14:40 localhost kernel: [29631.692010] PM: resume of drv:usb dev:5-1 complete after 474.954 msecs
May 26 19:14:40 localhost kernel: [29631.953046] usb 5-1.3: reset low speed USB device using uhci_hcd and address 3
May 26 19:14:40 localhost kernel: [29632.263047] PM: resume of drv:usb dev:5-1.3 complete after 571.028 msecs
May 26 19:14:40 localhost kernel: [29632.353047] usb 5-1.4: reset full speed USB device using uhci_hcd and address 4
May 26 19:14:40 localhost kernel: [29632.479047] snd-usb-audio 5-1.4:1.0: no reset_resume for driver snd-usb-audio?
May 26 19:14:40 localhost kernel: [29632.479050] snd-usb-audio 5-1.4:1.1: no reset_resume for driver snd-usb-audio?
May 26 19:14:40 localhost kernel: [29632.479052] snd-usb-audio 5-1.4:1.2: no reset_resume for driver snd-usb-audio?
May 26 19:14:40 localhost kernel: [29632.480351] PM: resume of drv:usb dev:5-1.4 complete after 217.294 msecs
May 26 19:14:40 localhost kernel: [29632.480404] PM: resume of devices complete after 12525.179 msecs
May 26 19:14:40 localhost kernel: [29632.532491] PM: resume devices took 12.580 seconds
May 26 19:14:40 localhost kernel: [29632.532492] ------------[ cut here ]------------
May 26 19:14:40 localhost kernel: [29632.532498] WARNING: at /build/buildd/linux-2.6.32/kernel/power/suspend_test.c:53 suspend_test_finish+0x89/0x90()
May 26 19:14:40 localhost kernel: [29632.532499] Hardware name: EP35-DS3L
May 26 19:14:40 localhost kernel: [29632.532501] Component: resume devices, time: 12580
May 26 19:14:40 localhost kernel: [29632.532502] Modules linked in: binfmt_misc vboxnetadp vboxnetflt vboxdrv reiserfs xt_limit xt_tcpudp ipt_LOG ipt_MASQUERADE xt_DSCP ipt_REJECT nf_conntrack_irc nf_conntrack_ftp xt_state iptable_nat nf_nat nf_conntrack_ipv4 snd_hda_codec_realtek nf_conntrack nf_defrag_ipv4 iptable_mangle iptable_filter ppdev usbhid ip_tables x_tables hid parport_pc fbcon tileblit font bitblit softcursor uvcvideo videodev v4l1_compat usb_storage coretemp it87 hwmon_vid snd_hda_intel snd_usb_audio snd_usb_lib snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd lp intel_agp soundcore snd_page_alloc nvidia(P) vga16fb vgastate parport agpgart floppy 3w_xxxx pata_jmicron r8169 mii
May 26 19:14:40 localhost kernel: [29632.532540] Pid: 10870, comm: pm-suspend Tainted: P        W  2.6.32-22-generic #33-Ubuntu
May 26 19:14:40 localhost kernel: [29632.532541] Call Trace:
May 26 19:14:40 localhost kernel: [29632.532545]  [<c014c3d2>] warn_slowpath_common+0x72/0xa0
May 26 19:14:40 localhost kernel: [29632.532548]  [<c0183b19>] ? suspend_test_finish+0x89/0x90
May 26 19:14:40 localhost kernel: [29632.532550]  [<c0183b19>] ? suspend_test_finish+0x89/0x90
May 26 19:14:40 localhost kernel: [29632.532553]  [<c014c44b>] warn_slowpath_fmt+0x2b/0x30
May 26 19:14:40 localhost kernel: [29632.532555]  [<c0183b19>] suspend_test_finish+0x89/0x90
May 26 19:14:40 localhost kernel: [29632.532557]  [<c01838f1>] suspend_devices_and_enter+0xa1/0xd0
May 26 19:14:40 localhost kernel: [29632.532561]  [<c0588f82>] ? printk+0x1d/0x23
May 26 19:14:40 localhost kernel: [29632.532563]  [<c01839dd>] enter_state+0xbd/0xf0
May 26 19:14:40 localhost kernel: [29632.532566]  [<c0183095>] state_store+0x75/0xc0
May 26 19:14:40 localhost kernel: [29632.532568]  [<c0183020>] ? state_store+0x0/0xc0
May 26 19:14:40 localhost kernel: [29632.532571]  [<c034ba80>] kobj_attr_store+0x20/0x30
May 26 19:14:40 localhost kernel: [29632.532574]  [<c025e0b5>] sysfs_write_file+0x95/0x100
May 26 19:14:40 localhost kernel: [29632.532577]  [<c0207bf2>] vfs_write+0xa2/0x1a0
May 26 19:14:40 localhost kernel: [29632.532579]  [<c025e020>] ? sysfs_write_file+0x0/0x100
May 26 19:14:40 localhost kernel: [29632.532582]  [<c058db20>] ? do_page_fault+0x160/0x3a0
May 26 19:14:40 localhost kernel: [29632.532584]  [<c0208512>] sys_write+0x42/0x70
May 26 19:14:40 localhost kernel: [29632.532586]  [<c01033ec>] syscall_call+0x7/0xb
May 26 19:14:40 localhost kernel: [29632.532588] ---[ end trace 13a03cd2332622b1 ]---
May 26 19:14:40 localhost kernel: [29632.532621] Restarting tasks ... done.
May 26 19:14:41 localhost kernel: [29633.321830] 3w-xxxx: scsi5: Unknown scsi opcode: 0x85
May 26 19:14:41 localhost kernel: [29633.321851] 3w-xxxx: scsi5: Unknown scsi opcode: 0x85
May 26 19:14:56 localhost gnome-screensaver-dialog: pam_sm_authenticate: Called
May 26 19:14:56 localhost gnome-screensaver-dialog: pam_sm_authenticate: username = [rob]
May 26 19:15:35 localhost kernel: [29687.988018] sd 5:0:0:0: WARNING: Command (0x28) timed out, resetting card.
```

It seemed faster from the command line. About 1m45s but I was still waiting after 5mins to be able to scroll. I am going to look at my video card settings in the bios.

---

### Post by platosearwax on 2010-05-26
Sounds like the problems I used to have in KDE using Dolphin in OpenSUSE.  Never got a solution to that one either (other than to switch to Ubuntu and GNOME :)). My 5 year old desktop with Lucid and Nautilus takes about 5 seconds to load /usr/lib to the point I can scroll and about 40 seconds to load up all the files.

---

### Post by Robbyx on 2010-05-26
I have adjusted my bios settings for the dram to auto and the pcexpress to 100.  Nautilus loaded faster and it was easier to go to the lib directory. The directory itself would not scroll down and I gave up. 

I then tried disk useage analyzer and that had no problems opening the lib or any of the sub directories. 

What is going wrong? As  I said earlier in the past I have used alternate file managers but I can't do that now because subdirectories will not open when I click on them.

---

### Post by Robbyx on 2010-05-27
I have just installed xfe and am shocked at its speed. It opens the problem directories instantly and can deal with sub directories.

---

### Post by platosearwax on 2010-05-27
> **Robbyx said:**
> I have just installed xfe and am shocked at its speed. It opens the problem directories instantly and can deal with sub directories.

Holy moly, that thing is fast.  That might be my new file manager.  Thanks for that!

---

### Post by philinux on 2010-05-27
I'm liking pcmanfm. Tools section is great.

Opens /usr/lib instantly.

---

### Post by Robbyx on 2010-05-27
> **philinux said:**
> I'm liking pcmanfm. Tools section is great.

Opens /usr/lib instantly.

Assuming pcman is that the same as pcmanfm I can not open subdirectories with it. Same problem with Thunar. Ok with xfe.

---

### Post by Robbyx on 2010-05-27
> **platosearwax said:**
> Holy moly, that thing is fast.  That might be my new file manager.  Thanks for that!

See my correspondence with the author:

[http://ubuntuforums.org/showthread.php?p=9370333#post9370333](http://ubuntuforums.org/showthread.php?p=9370333#post9370333)

---

### Post by PCMan on 2010-05-30
> **Robbyx said:**
> See my correspondence with the author:

[http://ubuntuforums.org/showthread.php?p=9370333#post9370333](http://ubuntuforums.org/showthread.php?p=9370333#post9370333)

The issue was fixed in the latest releases of PCManFM.
If you are suffereing from speed problem and haven't find a good enough solution, try PCManFM 0.9.7.
[http://blog.lxde.org/?p=727](http://blog.lxde.org/?p=727)

This is one of the fastest gtk2-based file manager which fully support tabbed browsing, gio/gvfs, and new desktop standards. The latest version could work as a dropped in replacement for nautilus.

Please report bugs if it doesn't work for you.

---

### Post by ammonkey on 2010-06-01
Hello PCMan,

Yes pcmanfm is fast it open a window instantly but it don't load content directories faster than nautilus. loading /usr/bin or /usr/lib take a while too in pcmanfm. It suffers from the same problem nautilus got, loading all the gvfs attributes.

Try loading a few number of attributes and u'll see the loading speed drastically increase. So i don't know what could be a solution, a gio/gvfs improvement? or that the filemanagers only request a few attributes to increase loading directories speed and grab the rest of the attributes in the background or only when it's needed?

Ps: i only tried the 0.9.6 version of pcmanfm a few days ago.

---

### Post by PCMan on 2010-06-05
> **ammonkey said:**
> Hello PCMan,

Yes pcmanfm is fast it open a window instantly but it don't load content directories faster than nautilus. loading /usr/bin or /usr/lib take a while too in pcmanfm. It suffers from the same problem nautilus got, loading all the gvfs attributes.

Try loading a few number of attributes and u'll see the loading speed drastically increase. So i don't know what could be a solution, a gio/gvfs improvement? or that the filemanagers only request a few attributes to increase loading directories speed and grab the rest of the attributes in the background or only when it's needed?

Ps: i only tried the 0.9.6 version of pcmanfm a few days ago.
You assumption is not correct.
Nautilus and gvfs does load most attributes. PCManFM doesn't. It only does the I/O required. Testing /usr/bin is an extreme case. This is limited due to the design of UNIX. Executables are recognized according to permissio, but there is no way to know if it's a shell script, python script, perl, or a elf binary. The only way to know this is to read the files. There is no way to speed up this operation. If you test others, such as home dir or even better an remote one, pcmanfm will be significantly faster.

---

