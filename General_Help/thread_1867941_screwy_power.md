---
title: "screwy power"
date: 2011-10-23
forum: General Help
---

### Post by fish tank on 2011-10-23
I am having trouble getting my ubuntu 10.04 natty to use less electricity.

I see no evidence that the processor is genuinely sleeping when idle. A kill-a-watt meter connected before the (Antec FP-150-8) power supply just sticks at about 51W regardless of anything I do. It's supposed to be a low power mobo (DH67CF mini-ITX) and processor (i3-2100T).  Any diagnostic suggestions would be welcome. I have run out of ideas and fear buying another PSU when I may still have a software problem.

I expect to see processor C state details listed by 'cat  /proc/acpi/processor/*/power' but I find that I don't even have a '/proc/acpi/processor/' directory. I have an intel processor so I have tried using intel_idle and acpi_idle in the kernel. Neither seem to give me the directory or actually do anything.[FONT=&quot]

[/FONT]**!ls -al /proc/acpi/**
total 0
dr-xr-xr-x   4 root root 0 2011-10-23 18:59 .
dr-xr-xr-x 144 root root 0 2011-10-23 18:59 ..
dr-xr-xr-x   2 root root 0 2011-10-23 19:07 ac_adapter
dr-xr-xr-x   2 root root 0 2011-10-23 19:07 battery
-r--------   1 root root 0 2011-10-23 18:59 event
-rw-r--r--   1 root root 0 2011-10-23 19:07 wakeup
**!ps|grep acpi**
917    acpid -c /etc/acpi/events -s /var/run/acpid.socket
2038      grep --color=auto acpi[FONT=&quot]
[B]
I Attached some logs.
[/B][/FONT][FONT=&quot]
[/FONT]

---

