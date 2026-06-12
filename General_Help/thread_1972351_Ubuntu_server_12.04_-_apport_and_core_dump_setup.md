---
title: "Ubuntu server 12.04 - apport and core dump setup"
date: 2012-05-03
forum: General Help
---

### Post by mhoulier on 2012-05-03
Hi,

I've installed Ubuntu server 12.04 (64bit).
I see that Apport is enable by default in /etc/default/apport.
And crash info are being passed down to Apport in /proc/sys/kernel/core_pattern.

I've enabled core dump in /etc/security/limits.conf by adding:
```
*    soft    core    100000
```
I've checked that 'ulimit -c' returns the expected value (even after reboot).

- Do I need to do sthg else to get Apport working?

- Does it require a GUI installed to work?

At some point, I got "Illegal instruction (core dumped)" message, but there is nothing in /var/crash/.
- Is this expected?

(Also, note that this is while running Xen 4.1.2 with Ubuntu as Dom0)



Since I've never used Apport, I decided to dump cores directly to a folder.
For those interested, here are the steps I followed:

First, adding in /etc/sysctl.conf:
```
kernel.core_pattern = /var/crash/core.%e.%s.%p.%h.%t
kernel.core_uses_pid = 1
fs.suid_dumpable = 2
```

I'm not sure if this is the expected behavior,
but to make sure the system applies the changes to /proc/sys/kernel/core_pattern after a reboot,
I needed to disable Apport in /etc/default/apport.
(Otherwise core_pattern file was getting overwritten to force passing down the crash info to Apport)

Now, when I get the core dumped message, it does create the core file as expected.

---

