---
title: "Display wigs out on Ubuntu 11.04 /var/log/syslog output"
date: 2012-01-20
forum: General Help
---

### Post by s0c0 on 2012-01-20
Display wigs out on Ubuntu 11.04. Starts switching between all open application windows really fast and the screen flickers. No logs of note were found in Xorg.log.0. Here is output from /var/log/syslog:

[http://pastebin.com/C8T0jCxq]("http://pastebin.com/C8T0jCxq")

Any ideas? Running 64bit and here is my lspci -v output:

```


00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
	Subsystem: Intel Corporation Device 2002
	Flags: bus master, fast devsel, latency 0, IRQ 49
	Memory at fe000000 (64-bit, non-prefetchable) [size=4M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at f000 [size=64]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

```

---

### Post by dcstar on 2012-01-20
> **s0c0 said:**
> Display wigs out on Ubuntu 11.04. Starts switching between all open application windows really fast and the screen flickers. No logs of note were found in Xorg.log.0. Here is output from /var/log/syslog:

[http://pastebin.com/C8T0jCxq]("http://pastebin.com/C8T0jCxq")

Any ideas? Running 64bit and here is my lspci -v output:

```


00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
	Subsystem: Intel Corporation Device 2002
	Flags: bus master, fast devsel, latency 0, IRQ 49
	Memory at fe000000 (64-bit, non-prefetchable) [size=4M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at f000 [size=64]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

```

Do you have any BIOS options for changing the video settings? Is your system fully updated?

---

