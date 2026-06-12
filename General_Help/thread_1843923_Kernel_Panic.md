---
title: "Kernel Panic"
date: 2011-09-14
forum: General Help
---

### Post by elbenja on 2011-09-14
Hello,
After loading using grub:

```

run-init : /sbin/init: no such file or directory
Kernel panic - not syncing : Attempted to kill init
Pid: 1, comm: run-init not tainted 2.6.38-11-generic #48-ubuntu
Call trace:
<hex> ? panic + 0x91/0x19c
<hex> ? forget_original_parent + 0x263/0x270
<hex> ? exit_notify + 0x1b/0x180
<hex> ? do_exit + 0x1d3/0x410
<hex> ? sys_write + 0x51/0x90
<hex> ? sys_exit + 0x17/0x20
<hex> ? system_call_fastpath + 0x16/0x1b

```

I can access the partition using a Kubuntu live CD.
I've run fsck.
"/sbin/init" exists in the partition ...
With a Grub Live CD I can boot, but the same problem occurs.
What else can I do?,
I don't want to reinstall the system again.

Thanks

---

### Post by Cinelli on 2012-03-26
> **elbenja said:**
> Hello,
After loading using grub:

```

run-init : /sbin/init: no such file or directory
Kernel panic - not syncing : Attempted to kill init
Pid: 1, comm: run-init not tainted 2.6.38-11-generic #48-ubuntu
Call trace:
<hex> ? panic + 0x91/0x19c
<hex> ? forget_original_parent + 0x263/0x270
<hex> ? exit_notify + 0x1b/0x180
<hex> ? do_exit + 0x1d3/0x410
<hex> ? sys_write + 0x51/0x90
<hex> ? sys_exit + 0x17/0x20
<hex> ? system_call_fastpath + 0x16/0x1b

```I can access the partition using a Kubuntu live CD.
I've run fsck.
"/sbin/init" exists in the partition ...
With a Grub Live CD I can boot, but the same problem occurs.
What else can I do?,
I don't want to reinstall the system again.

Thanks

Download a copy of Unetbootin and install Hiren's Boot CD to a usb stick and boot from that. There should be plenty of tools included in that package to get you going again.

---

