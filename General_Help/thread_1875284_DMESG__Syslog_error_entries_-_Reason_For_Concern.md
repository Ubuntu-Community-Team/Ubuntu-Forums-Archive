---
title: "DMESG / Syslog error entries - Reason For Concern?"
date: 2011-11-04
forum: General Help
---

### Post by BludGeonT on 2011-11-04
Hello everyone, I've got a couple of questions to ask based off of some information I've seen from dmesg and syslog output.

Would anyone happen to know off hand if these messages are something to be concerned about?

Kernel Version:
Linux irvmdb05 2.6.38-8-server #42-Ubuntu SMP Mon Apr 11 03:49:04 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

Server Specs:

Handle 0x0100, DMI type 1, 27 bytes
System Information
        Manufacturer: HP
        Product Name: ProLiant DL380 G7
BIOS Information
        Vendor: HP
        Version: P67
        Release Date: 05/05/2011

120GB RAM

OS:  Ubuntu 11.04


-----

Brief Description:

We were running heavy load on this system with a MongoDB migration and started to notice connection timeouts on the system.  They seemed to coincide with these entries within dmesg/syslog - just possibly coincidence but I wanted to run it by the community to see what suggestions could be made.

Thank you.
------------

Messages seen in DMESG:

[1131516.069427] ACPI Error: SMBus or IPMI write requires Buffer of length 66, found length 32 (20110112/exfield-285 )
[1131516.069433] ACPI Error: Method parse/execution failed [\_SB_.PMI0._PMM] (Node ffff880ea888e7f8 ), AE_AML_BUFFER_LIMIT (20110112/psparse-536 )
[1131516.069443] ACPI Exception: AE_AML_BUFFER_LIMIT, Evaluating _PMM (20110112/power_meter-348 )
[1131563.525531] ACPI Error: SMBus or IPMI write requires Buffer of length 66, found length 32 (20110112/exfield-285 )
[1131563.525537] ACPI Error: Method parse/execution failed [\_SB_.PMI0._PMM] (Node ffff880ea888e7f8 ), AE_AML_BUFFER_LIMIT (20110112/psparse-536 )
[1131563.525548] ACPI Exception: AE_AML_BUFFER_LIMIT, Evaluating _PMM (20110112/power_meter-348 )

-----------------

SYSLOG Entries:

Nov  3 16:52:36 irvmdb05 mcelog: Unsupported new Family 6 Model 2c CPU: only decoding architectural errors
Nov  3 16:52:36 irvmdb05 mcelog: failed to prefill DIMM database from DMI data

...

Nov  3 17:15:18 irvmdb05 kernel: [1131563.525531] ACPI Error: SMBus or IPMI write requires Buffer of length 66, found length 32 (20110112/exfield-285)
Nov  3 17:15:18 irvmdb05 kernel: [1131563.525537] ACPI Error: Method parse/execution failed [\_SB_.PMI0._PMM] (Node ffff880ea888e7f8 ), AE_AML_BUFFER_LIMIT (20110112/psparse-536 )
Nov  3 17:15:18 irvmdb05 kernel: [1131563.525548] ACPI Exception: AE_AML_BUFFER_LIMIT, Evaluating _PMM (20110112/power_meter-348 )

---

### Post by lptr on 2012-03-09
Would like to know if you found a solution to this? Have same entries here on a HP DL server running 10.04.3 LTS

```
ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PMI0._PMM] (Node ffff880216c51a20), AE_AML_BUFFER_LIMIT
``````
Linux version 2.6.32-33-server (buildd@allspice) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #72-Ubuntu SMP Fri Jul 29 21:21:55 UTC 2011
```

---

