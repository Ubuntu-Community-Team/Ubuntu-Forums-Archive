---
title: "Mysterious freeze"
date: 2010-10-25
forum: General Help
---

### Post by evenrelation on 2010-10-25
I'm running Lucid on an almost brand new Lenovo TP Edge laptop. Lately, it has been freezing occasionally without me having the slightest idea why. Sometimes I have been working with a particular program, and sometimes the laptop has been sitting idle. I've tried to close down some background programs and processes, but it still keeps freezing.

I get a black screen, sometimes grey and sometimes with stripes. It's not just the screen since Ctrl+Alt+Delate and Enter would begin the shut down process, which it doesn't. Then, my only option is to restart completely.

I'll note that it's not all that annoying so far since it doesn't happen all that frequently...yet.

But does anyone have an idea of, say, a log file that might indicate the source of the problem?

I'd hate it if it was a hardware problem, since I'm in another country to which the one I bought it from.

---

### Post by Hippytaff on 2010-10-25
dmesg or syslog might shed some light.

They're all held in /var/log

---

### Post by Rubi1200 on 2010-10-25
What graphics card do you have installed and how much RAM does the system have available?

Also, take a look here for troubleshooting options:
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

You might also want to investigate whether something like Compiz or Conky (if you have it installed) could be causing problems.

---

### Post by evenrelation on 2010-10-25
> **Rubi1200 said:**
> What graphics card do you have installed and how much RAM does the system have available?

Also, take a look here for troubleshooting options:
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

You might also want to investigate whether something like Compiz or Conky (if you have it installed) could be causing problems.

What were the terminal commands for hardware and memory info? There's no way I can remember those things.

I have Compiz (but not Conky) installed. I'm not much of a fan of visual effects so I'm pretty sure I've already figured configured that sort of stuff out.

And that link is great. I'll try to have a look at it when I have the time.

---

### Post by evenrelation on 2010-10-25
```
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
``````
             total       used       free     shared    buffers     cached
Mem:          2770       2696         74          0         72       1675
-/+ buffers/cache:        947       1822
Swap:         8118          0       8118
```

---

### Post by evenrelation on 2010-10-26
I turned on my laptop at around 10ish this morning, put it on suspend, and then turned it back on at around 13:45. It froze almost immediately after I wrote down the password and I had to restart manually (turning off and then on).

From syslog:

```
Oct 26 13:46:13 -laptop kernel: [ 3062.206723] PM: Syncing filesystems ... done.
Oct 26 13:46:13 -laptop kernel: [ 3062.214780] PM: Preparing system for mem sleep
Oct 26 13:46:13 -laptop kernel: [ 3062.214786] Freezing user space processes ... (elapsed 0.00 seconds) done.
Oct 26 13:46:13 -laptop kernel: [ 3062.216088] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
Oct 26 13:46:13 -laptop kernel: [ 3062.216202] PM: Entering mem sleep
Oct 26 13:46:13 -laptop kernel: [ 3062.216219] Suspending console(s) (use no_console_suspend to debug)
Oct 26 13:46:13 -laptop kernel: [ 3062.440725] PM: suspend of drv:psmouse dev:serio5 complete after 224.068 msecs
Oct 26 13:46:13 -laptop kernel: [ 3062.456108] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Oct 26 13:46:13 -laptop kernel: [ 3062.456339] sd 0:0:0:0: [sda] Stopping disk
Oct 26 13:46:13 -laptop kernel: [ 3063.032398] PM: suspend of drv:sd dev:0:0:0:0 complete after 576.291 msecs
Oct 26 13:46:13 -laptop kernel: [ 3063.456710] PM: suspend of drv:psmouse dev:serio4 complete after 392.534 msecs
Oct 26 13:46:13 -laptop kernel: [ 3063.864070] PM: suspend of drv:atkbd dev:serio0 complete after 407.344 msecs
Oct 26 13:46:13 -laptop kernel: [ 3063.866443] ACPI handle has no context!
Oct 26 13:46:13 -laptop kernel: [ 3063.866505] ============> r8192E suspend call.
Oct 26 13:46:13 -laptop kernel: [ 3063.866508] RTL819XE:UI is open out of suspend function
Oct 26 13:46:13 -laptop kernel: [ 3063.866510] r8192E support WOL call??????????????????????
Oct 26 13:46:13 -laptop kernel: [ 3063.866623] rtl819xSE 0000:03:00.0: PCI INT A disabled
Oct 26 13:46:13 -laptop kernel: [ 3063.866686] ACPI handle has no context!
Oct 26 13:46:13 -laptop kernel: [ 3063.866693] ACPI handle has no context!
Oct 26 13:46:13 -laptop kernel: [ 3064.004090] HDA Intel 0000:01:05.1: PCI INT B disabled
Oct 26 13:46:13 -laptop kernel: [ 3064.004113] ACPI handle has no context!
Oct 26 13:46:13 -laptop kernel: [ 3064.020070] PM: suspend of drv:HDA Intel dev:0000:01:05.1 complete after 120.011 msecs
Oct 26 13:46:13 -laptop kernel: [ 3064.358654] radeon 0000:01:05.0: PCI INT A disabled
Oct 26 13:46:13 -laptop kernel: [ 3064.372082] PM: suspend of drv:radeon dev:0000:01:05.0 complete after 352.003 msecs
Oct 26 13:46:13 -laptop kernel: [ 3064.477008] HDA Intel 0000:00:14.2: PCI INT A disabled
Oct 26 13:46:13 -laptop kernel: [ 3064.477049] ACPI handle has no context!
Oct 26 13:46:13 -laptop kernel: [ 3064.492071] PM: suspend of drv:HDA Intel dev:0000:00:14.2 complete after 119.961 msecs
Oct 26 13:46:13 -laptop kernel: [ 3064.492088] ehci_hcd 0000:00:13.2: PCI INT B disabled
Oct 26 13:46:13 -laptop kernel: [ 3064.492100] ohci_hcd 0000:00:13.1: PCI INT A disabled
Oct 26 13:46:13 -laptop kernel: [ 3064.492111] ohci_hcd 0000:00:13.0: PCI INT A disabled
Oct 26 13:46:13 -laptop kernel: [ 3064.492122] ehci_hcd 0000:00:12.2: PCI INT B disabled
Oct 26 13:46:13 -laptop kernel: [ 3064.492134] ohci_hcd 0000:00:12.1: PCI INT A disabled
Oct 26 13:46:13 -laptop kernel: [ 3064.492145] ohci_hOct 26 13:47:25 -laptop kernel: imklog 4.2.0, log source = /proc/kmsg started.
```

I can't make anything of those lines from syslog, and dmesg even less since there's no timing.

Any thoughts?

---

### Post by evenrelation on 2010-11-01
I hope I'm not reviving an old thread, but I have a feeling my laptop has been freezing because I so frequently put it on standby when I close the lid.

Just a thought for those who may have the same problem: Frequent standby's are not a good idea.

---

### Post by Hippytaff on 2010-11-01
You can alter the power managment options so that the laptop hibernates when you close the lid rather than suspends, that might be one work around.

---

### Post by evenrelation on 2010-11-01
> **Hippytaff said:**
> You can alter the power managment options so that the laptop hibernates when you close the lid rather than suspends, that might be one work around.

That's what I've been wondering lately.

Although this particular problem might disappear, I'm not sure frequent hibernation would be any more healthy or less damaging than frequent standby.

---

