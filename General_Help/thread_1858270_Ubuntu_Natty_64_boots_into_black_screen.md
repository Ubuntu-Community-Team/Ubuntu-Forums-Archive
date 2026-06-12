---
title: "Ubuntu Natty 64 boots into black screen"
date: 2011-10-12
forum: General Help
---

### Post by realstarman on 2011-10-12
My Ubuntu Natty 64bit boots into black screen. Grub appears and after selecting Ubuntu, there is a blinking cursor for some secs and then the black screen.
It's a dual boot and the other side (Windows 7) boots just fine.
When I edit the grub menu and  boot with acpi=off, Ubuntu boots just fine.

After install, Ubuntu didn't have these problems. Only after about 2 months usage, the problem started surfacing. I am trying to find out what I have done that could cause it.
Rather than a complete reinstall – which is a hassle because I am actively working on this machine and rebuilding it would cost me more than a day, I'd like to debug it. (besides, just reinstalling doesn't really tell me what's wrong, it's just potentially curing a symptom without revealing the cause).

Graphics Adapter is ATI. I am not running proprietary drivers. I tried this directly after the first install and ran into issues with Unity not coming up.

Laptop is a Lenovo Edge E520.

I checked syslog, and lshw, etc. but could not make sense of what I found and found no post on the www that could help me.
I am not new to Ubuntu but do not consider myself a power user or an expert (Rather a user with some experience and IT-knowledge).

Would appreciate any hint (besides reinstall the system).

Some info I used during my first attempts to find the root cause: 

Uname -a shows:
starman@thinky:/var/log$ uname -a
```
Linux thinky 2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:17:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```

I checked the syslog and found that the unsuccessful boot seems to stop while logging the RAM map:
```
Oct 12 06:38:35 thinky kernel: imklog 4.6.4, log source = /proc/kmsg started.
Oct 12 06:38:35 thinky rsyslogd: [origin software="rsyslogd" swVersion="4.6.4" x-pid="440" x-info="http://www.rsyslog.com"] (re)start
Oct 12 06:38:35 thinky rsyslogd: rsyslogd's groupid changed to 103
Oct 12 06:38:35 thinky rsyslogd: rsyslogd's userid changed to 101
Oct 12 06:38:35 thinky rsyslogd-2039: Could no open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Oct 12 06:38:35 thinky kernel: [    0.000000] Initializing cgroup subsys cpuset
Oct 12 06:38:35 thinky kernel: [    0.000000] Initializing cgroup subsys cpu
Oct 12 06:38:35 thinky kernel: [    0.000000] Linux version 2.6.38-11-generic (buildd@allspice) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) ) #50-Ubuntu SMP Mon Sep 12 21:17:25 UTC 2011 (Ubuntu 2.6.38-11.50-generic 2.6.38.8)
Oct 12 06:38:35 thinky kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-11-generic root=UUID=395a566b-9851-489f-976d-fee88fef92a0 ro quiet splash vt.handoff=7
Oct 12 06:38:35 thinky kernel: [    0.000000] BIOS-provided physical RAM map:
Oct 12 06:38:35 thinky kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d800 (usable)
Oct 12 06:38:35 thinky kernel: [    0.000000]  BIOS-e820: 000000000009d800 - 00000000000a0000 (reserved)
Oct 12 06:38:35 thinky kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Oct 12 06:38:35 thinky kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000ba99f000 (usable)
Oct 12 06:38:35 thinky kernel: [    0.000000]  BIOS-e820: 00000000ba99f000 - 00000000bae9f000 (reserved)
Oct 12 06:38:35 thinky kernel: [    0.000000]  BIOS-e820: 00000000bae9f000 - 00000000baf9f000 (ACPI NVS)
Oct 12 06:38:35 thinky kernel: [    0.000000]  BIOS-e820: 00000000baf9f000 - 00000000bafff000 (ACPI data)
Oct 12 06:38:35 thinky kernel: [    0.000000]  BIOS-e820: 00000000bafff000 - 00000000bb000000 (usable)
Oct 12 06:38:35 thinky kernel: [    0.000000]  BIOS-e820: 00000000bb000000 - 00000000bfa00000 (reserved)
Oct 12 06:38:35 thinky kernel: [    0.000000]  BIOS-e820: 00000000f8000000Oct 12 06:39:29 thinky kernel: imklog 4.6.4, log source = /proc/kmsg started.
Oct 12 06:39:29 thinky rsyslogd: [origin software="rsyslogd" swVersion="4.6.4" x-pid="470" x-info="http://www.rsyslog.com"] (re)start
Oct 12 06:39:29 thinky rsyslogd: rsyslogd's groupid changed to 103
Oct 12 06:39:29 thinky rsyslogd: rsyslogd's userid changed to 101
Oct 12 06:39:29 thinky rsyslogd-2039: Could no open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Oct 12 06:39:29 thinky kernel: [    0.000000] Initializing cgroup subsys cpuset
Oct 12 06:39:29 thinky kernel: [    0.000000] Initializing cgroup subsys cpu
Oct 12 06:39:29 thinky kernel: [    0.000000] Linux version 2.6.38-11-generic (buildd@allspice) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) ) #50-Ubuntu SMP Mon Sep 12 21:17:25 UTC 2011 (Ubuntu 2.6.38-11.50-generic 2.6.38.8)
Oct 12 06:39:29 thinky kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-11-generic root=UUID=395a566b-9851-489f-976d-fee88fef92a0 ro quiet splash vt.handoff=7 acpi=off
… <continue with successful boot>

```

lshw shows for display:
```
           *-display UNCLAIMED
                description: VGA compatible controller
                product: NI Whistler [AMD Radeon HD 6600M Series]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller cap_list
                configuration: latency=0
                resources: memory:c0000000-cfffffff memory:e2600000-e261ffff ioport:5000(size=256) memory:e2620000-e263ffff
        *-display
             description: VGA compatible controller
             product: 2nd Generation Core Processor Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:18 memory:e0000000-e03fffff memory:d0000000-dfffffff ioport:6000(size=64)

```

---

### Post by realstarman on 2011-10-14
Anybody with some system/debugging knowledge willing to help?

---

### Post by effenberg0x0 on 2011-10-14
Hybrid Graphics. Not my specialty, unfortunately. But Ubuntu docs has a section for it:
[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

Regards,
Effenberg

---

### Post by realstarman on 2011-10-19
Not sure, if this is the root cause though. 

Kernel seems to be ok:

```
starman@thinky:~$ sudo grep -i switcheroo /boot/config-2.6.*
Password: **

/boot/config-2.6.38-10-generic:CONFIG_VGA_SWITCHEROO=y
/boot/config-2.6.38-11-generic:CONFIG_VGA_SWITCHEROO=y
/boot/config-2.6.38-8-generic:CONFIG_VGA_SWITCHEROO=y

```
But switcheroo is not enabled (no switch file):

```
starman@thinky:~$ sudo ls -l /sys/kernel/
insgesamt 0
drwx------  15 root root    0 2011-10-19 08:22 debug
-r--r--r--   1 root root 4096 2011-10-19 06:30 kexec_crash_loaded
-rw-r--r--   1 root root 4096 2011-10-19 06:30 kexec_crash_size
-r--r--r--   1 root root 4096 2011-10-19 06:30 kexec_loaded
drwxr-xr-x   4 root root    0 2011-10-19 06:30 mm
-r--r--r--   1 root root  380 2011-10-19 06:30 notes
-rw-r--r--   1 root root 4096 2011-10-19 06:30 profiling
drwxr-xr-x   3 root root    0 2011-10-19 08:22 security
drwxr-xr-x 106 root root    0 2011-10-19 08:23 slab
-rw-r--r--   1 root root 4096 2011-10-19 06:30 uevent_helper
-r--r--r--   1 root root 4096 2011-10-19 08:22 uevent_seqnum
-r--r--r--   1 root root 4096 2011-10-19 06:30 vmcoreinfo
```

Not sure what I should do now....

---

### Post by KingYaba on 2011-10-19
I get this problem, on rare occasions, when I installed updates during the previous session. Something about it boinking x because when I'm in CLI the command startx won't work. Boot Ubuntu into failsafe graphic mode and uninstall your ATI driver. Reboot regularly and reinstall. Then reboot again. :D

Go to the AMD/ATI website and try the proprietary driver. 

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

Follow the instructions from the Wiki. 

[http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)

---

### Post by realstarman on 2011-10-24
Upgraded to oneiric. Boot works now (but screen resolution is wrong and cannot install ATI driver -> new thread).

Thanks for the help so far.

---

