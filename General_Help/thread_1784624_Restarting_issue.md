---
title: "Restarting issue"
date: 2011-06-17
forum: General Help
---

### Post by TGLewis on 2011-06-17
Hello everyone!

I'm new here, so please bear with my noob-ness.
I've been having an issue with my Ubuntu computer rebooting itself at exactly the same time each day. I'll post a snippet of the logs around the time with this post. I'm wondering how I can stop it from happening, as it's running as a server and is causing a bit of an issue. There are no stray crons etc, been through all that.

```

Jun 15 08:01:10 name kernel: imklog 4.6.4, log source = /proc/kmsg started.
Jun 15 08:01:10 name kernel: [    0.000000] Initializing cgroup subsys cpuset
Jun 15 08:01:10 name kernel: [    0.000000] Initializing cgroup subsys cpu
Jun 15 08:01:10 name kernel: [    0.000000] Linux version 2.6.38-8-generic (buildd@vernadsky) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)
Jun 15 08:01:10 name kernel: [    0.000000] BIOS-provided physical RAM map:
Jun 15 08:01:10 name kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Jun 15 08:01:10 name kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Jun 15 08:01:10 name kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Jun 15 08:01:10 name kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003f770000 (usable)
Jun 15 08:01:10 name kernel: [    0.000000]  BIOS-e820: 000000003f770000 - 000000003f77a000 (ACPI data)
Jun 15 08:01:10 name kernel: [    0.000000]  BIOS-e820: 000000003f77a000 - 000000003f780000 (ACPI NVS)
Jun 15 08:01:10 name kernel: [    0.000000]  BIOS-e820: 000000003f780000 - 0000000040000000 (reserved)
Jun 15 08:01:10 name kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Jun 15 08:01:10 name kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Jun 15 08:01:10 name kernel: [    0.000000]  BIOS-e820: 00000000ff800000 - 0000000100000000 (reserved)
Jun 15 08:01:10 name kernel: [    0.000000] Notice: NX (Execute Disable) protection missing in CPU!

```Any help would be greatly appreciated. I can't work this out.

Thanks! :D

---

### Post by TGLewis on 2011-06-17
Bump.

---

### Post by Yellow Pasque on 2011-06-17
I would try the server kernel and see if it does the same thing.

---

### Post by TGLewis on 2011-06-17
That's not really what I'm looking to do. I've already got everything set up. :(

---

### Post by TGLewis on 2011-06-17
Another bump.

---

### Post by TGLewis on 2011-06-18
Bump.

---

### Post by fdrake on 2011-06-18
did this happen after compiling the kernel? or just like that with no reason? if the first one u may need to recompile some modules.

---

### Post by TGLewis on 2011-06-18
It seemed to start happening completely randomly.

---

### Post by fdrake on 2011-06-18
what does the log file says?

less /var/log/messages |grep 08:01

08:01 - i think thats the time it reboots right?

---

### Post by TGLewis on 2011-06-18
Around 8:01, yes.
I can't see that log file in the /log directory. Could it be somewhere else?

---

### Post by fdrake on 2011-06-18
> **TGLewis said:**
> Around 8:01, yes.
I can't see that log file in the /log directory. Could it be somewhere else?

from the terminal

```
gnome-system-log
```

and look for 'messages' category around to that time

---

### Post by TGLewis on 2011-06-18
>  gnome-system-log-CRITICAL **: Unable to parse arguments: Cannot open display:

I'm using XFCE if it makes any difference, but it's headless.

---

