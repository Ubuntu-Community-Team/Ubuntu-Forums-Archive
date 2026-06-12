---
title: "boot crash  at battery state"
date: 2011-10-27
forum: General Help
---

### Post by sidewalkcynic on 2011-10-27
this is the message I get after the splash screen

```
Stopping restore sound card(s') mixer state(s)

PulseAudio configured . . .     [ok]

Saned disabled . . .            [ok]

Checking battery state          [ok]
```

syslog:
```
Oct 27 17:10:32 psycho-circuits rsyslogd: [origin software="rsyslogd" swVersion="5.8.1" x-pid="848" x-info="http://www.rsyslog.com"] start
Oct 27 17:10:32 psycho-circuits rsyslogd: rsyslogd's groupid changed to 103
Oct 27 17:10:32 psycho-circuits rsyslogd: rsyslogd's userid changed to 101
Oct 27 17:10:32 psycho-circuits rsyslogd-2039: Could no open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Oct 27 17:10:32 psycho-circuits kernel: [    0.000000] Initializing cgroup subsys cpuset
Oct 27 17:10:32 psycho-circuits kernel: [    0.000000] Initializing cgroup subsys cpu
Oct 27 17:10:32 psycho-circuits kernel: [    0.000000] Linux version 3.0.0-12-generic (buildd@vernadsky) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 (Ubuntu 3.0.0-12.20-generic 3.0.4)
Oct 27 17:10:32 psycho-circuits kernel: [    0.000000] KERNEL supported cpus:
Oct 27 17:10:32 psycho-circuits kernel: [    0.000000]   Intel GenuineIntel
Oct 27 17:10:32 psycho-circuits kernel: [    0.000000]   AMD AuthenticAMD
Oct 27 17:10:32 psycho-circuits kernel: [    0.000000]   NSC Geode by NSC
Oct 27 17:10:32 psycho-circuits kernel: [    0.000000]   Cyrix CyrixInstead
Oct 27 17:10:32 psycho-circuits kernel: [    0.000000]   Centaur CentaurHauls
Oct 27 17:10:32 psycho-circuits kernel: [    0.000000]   Transmeta GenuineTMx86
Oct 27 17:10:32 psycho-circuits kernel: [    0.000000]   Transmeta TransmetaCPU
Oct 27 17:10:32 psycho-circuits kernel: [    0.000000]   UMC UMC UMC UMC
Oct 27 17:10:32 psycho-circuits kernel: [    0.000000] Atom PSE erratum detected, BIOS microcode update recommended
Oct 27 17:10:32 psycho-circuits kernel: [    0.000000] Disabled fast string operations
Oct 27 17:10:32 psycho-circuits kernel: [    0.000000] BIOS-provided physical RAM map:
Oct 27 17:10:32 psycho-circuits kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Oct 27 17:10:32 psycho-circuits kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Oct 27 17:10:32 psycho-circuits kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Oct 27 17:10:32 psycho-circuits kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003f376000 (usable)
Oct 27 17:10:32 psycho-circuits kernel: [    0.000000]  BIOS-e820: 000000003f376000 - 000000003f3bf000 (reserved)
Oct 27 17:10:32 psycho-circuits kernel: [    0.000000]  BIOS-e820: 000000003f3bf000 - 000000003f46d000 (usable)
Oct 27 17:10:32 psycho-circuits kernel: [    0.000000]  BIOS-e820: 000000003f46d000 - 000000003f4bf000 (ACPI NVS)
Oct 27 17:10:32 psycho-circuits kernel: [    0.000000]  BIOS-e820: 000000003f4bf000 - 000000003f4f0000 (usable)
Oct 27 17:10:32 psycho-circuits kernel: [    0.000000]  BIOS-e820: 000000003f4f0000 - 000000003f4ff000 (ACPI data)
Oct 27 17:10:32 psycho-circuits kernel: [    0.000000]  BIOS-e820: 000000003f4ff000 - 000000003f500000 (usable)
Oct 27 17:10:32 psycho-circuits kernel: [    0.000000]  BIOS-e820: 000000003f500000 - 0000000040000000 (reserved)
Oct 27 17:10:32 psycho-circuits kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Oct 27 17:10:32 psycho-circuits kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Oct 27 17:10:32 psycho-circuits kernel: [    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
Oct 27 17:10:32 psycho-circuits kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
Oct 27 17:10:32 psycho-circuits kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Oct 27 17:10:32 psycho-circuits kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Oct 27 17:10:32 psycho-circuits kernel: [    0.000000] Notice: NX (Execute Disable) protection missing in CPU!
Oct 27 17:10:32 psycho-circuits kernel: [    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
Oct 27 17:10:32 psycho-circuits kernel: [Oct 27 17:15:33 psycho-circuits kernel: imklog 5.8.1, log source = /proc/kmsg started.
Oct 27 17:15:33 psycho-circuits rsyslogd: [origin software="rsyslogd" swVersion="5.8.1" x-pid="853" x-info="http://www.rsyslog.com"] start
Oct 27 17:15:33 psycho-circuits rsyslogd: rsyslogd's groupid changed to 103
Oct 27 17:15:33 psycho-circuits rsyslogd: rsyslogd's userid changed to 101
Oct 27 17:15:33 psycho-circuits rsyslogd-2039: Could no open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Oct 27 17:15:33 psycho-circuits kernel: [    0.000000] Initializing cgroup subsys cpuset
Oct 27 17:15:33 psycho-circuits kernel: [    0.000000] Initializing cgroup subsys cpu
Oct 27 17:15:33 psycho-circuits kernel: [    0.000000] Linux version 3.0.0-12-generic (buildd@vernadsky) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 (Ubuntu 3.0.0-12.20-generic 3.0.4)
Oct 27 17:15:33 psycho-circuits kernel: [    0.000000] KERNEL supported cpus:
Oct 27 17:15:33 psycho-circuits kernel: [    0.000000]   Intel GenuineIntel
Oct 27 17:15:33 psycho-circuits kernel: [    0.000000]   AMD AuthenticAMD
Oct 27 17:15:33 psycho-circuits kernel: [    0.000000]   NSC Geode by NSC
Oct 27 17:15:33 psycho-circuits kernel: [    0.000000]   Cyrix CyrixInstead
Oct 27 17:15:33 psycho-circuits kernel: [    0.000000]   Centaur CentaurHauls
Oct 27 17:15:33 psycho-circuits kernel: [    0.000000]   Transmeta GenuineTMx86
Oct 27 17:15:33 psycho-circuits kernel: [    0.000000]   Transmeta TransmetaCPU
Oct 27 17:15:33 psycho-circuits kernel: [    0.000000]   UMC UMC UMC UMC
Oct 27 17:15:33 psycho-circuits kernel: [    0.000000] Atom PSE erratum detected, BIOS microcode update recommended
Oct 27 17:15:33 psycho-circuits kernel: [    0.000000] Disabled fast string operations
Oct 27 17:15:33 psycho-circuits kernel: [    0.000000] BIOS-provided physical RAM map:
Oct 27 17:15:33 psycho-circuits kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Oct 27 17:15:33 psycho-circuits kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Oct 27 17:15:33 psycho-circuits kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Oct 27 17:15:33 psycho-circuits kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003f376000 (usable)
Oct 27 17:15:33 psycho-circuits kernel: [    0.000000]  BIOS-e820: 000000003f376000 - 000000003f3bf000 (reserved)
Oct 27 17:15:33 psycho-circuits kernel: [    0.000000]  BIOS-e820: 000000003f3bf000 - 000000003f46d000 (usable)
Oct 27 17:15:33 psycho-circuits kernel: [    0.000000]  BIOS-e820: 000000003f46d000 - 000000003f4bf000 (ACPI NVS)
Oct 27 17:15:33 psycho-circuits kernel: [    0.000000]  BIOS-e820: 000000003f4bf000 - 000000003f4f0000 (usable)
Oct 27 17:15:33 psycho-circuits kernel: [    0.000000]  BIOS-e820: 000000003f4f0000 - 000000003f4ff000 (ACPI data)
Oct 27 17:15:33 psycho-circuits kernel: [    0.000000]  BIOS-e820: 000000003f4ff000 - 000000003f500000 (usable)
Oct 27 17:15:33 psycho-circuits kernel: [    0.000000]  BIOS-e820: 000000003f500000 - 0000000040000000 (reserved)
Oct 27 17:15:33 psycho-circuits kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Oct 27 17:15:33 psycho-circuits kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Oct 27 17:15:33 psycho-circuits kernel: [    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
Oct 27 17:15:33 psycho-circuits kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
Oct 27 17:15:33 psycho-circuits kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Oct 27 17:15:33 psycho-circuits kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Oct 27 17:15:33 psycho-circuits kernel: [    0.000000] Notice: NX (Execute Disable) protection missing in CPU!
Oct 27 17:15:33 psycho-circuits kernel: [    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
Oct 27 17:15:33 psycho-circuits kernel: [

```

---

