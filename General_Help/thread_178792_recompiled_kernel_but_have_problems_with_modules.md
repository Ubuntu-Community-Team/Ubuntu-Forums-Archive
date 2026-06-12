---
title: "recompiled kernel but have problems with modules"
date: 2006-05-18
forum: General Help
---

### Post by eeyore on 2006-05-18
So I used this very fine HOWTO

[http://www.ubuntuforums.org/showthread.php?t=84174]("http://www.ubuntuforums.org/showthread.php?t=84174")

to recompile my kernel to the newest one (2.6.16.16)
First I should say that absolutely everything seems to be working for me. This is more of a concern than an actual problem. There have been a lot more error messages since the recompile one of which caught my eye only today

```
cat kern.log|grep modules
May 18 11:05:00 localhost kernel: No module symbols loaded - kernel modules not enabled.
```

This forced me to remember something about the compilation process. I needed to compile TOSHIBA_ACPI into the kernel as opposed to a module because my laptop stuff didn't seem to be working and that fixed the problem. Modprobing it didn't work either. I think it said the kernel module was missing.

A lot of other howtos include a make install_modules during the kernel compilation and there's no such thing here. Could that be the problem?

I've posted a few of the other errors below as well (frankly i'm surprised everything works)

dmesg output:
```
[4294688.810000] device-mapper: dm-linear: Device lookup failed
[4294688.810000] device-mapper: error adding target to table
[4294688.811000] device-mapper: dm-linear: Device lookup failed
[4294688.811000] device-mapper: error adding target to table
[4294688.812000] device-mapper: dm-linear: Device lookup failed
[4294688.812000] device-mapper: error adding target to table
[4294688.813000] device-mapper: dm-linear: Device lookup failed
[4294688.813000] device-mapper: error adding target to table
[4294688.824000] device-mapper: dm-linear: Device lookup failed
[4294688.824000] device-mapper: error adding target to table
[4294688.840000] device-mapper: dm-linear: Device lookup failed
[4294688.840000] device-mapper: error adding target to table
[4294688.840000] device-mapper: dm-linear: Device lookup failed
[4294688.840000] device-mapper: error adding target to table
[4294688.841000] device-mapper: dm-linear: Device lookup failed
[4294688.841000] device-mapper: error adding target to table
```

The things below I'm not sure are a result of the new kernel but I'll post them anyway because I've been snooping for errors everywhere. The ones before are definitely new because I didn't see them before on the startup console.

```
[4294669.319000] PCI: Cannot allocate resource region 4 of device 0000:00:1d.0
[4294669.319000] PCI: Cannot allocate resource region 4 of device 0000:00:1d.1
[4294669.319000] PCI: Cannot allocate resource region 4 of device 0000:00:1d.2
```

I also saw something somewhere else. I forget the command for showing all the pci components (I came across it a while ago), but that also had things like Unknown device in it all over the place.

AGAIN, everything is miraculously working after all of these=))
and rather fast. I love how little ram my linux machine uses as opposed to the windows setup I had. =)) I would love it if someone knew what the hell is up with the inner workings of the kernel.

---

### Post by xtacocorex on 2006-05-18
To list the PCI components, you need to type lspci at the command prompt.

---

### Post by towsonu2003 on 2006-05-18
> May 18 11:05:00 localhost kernel: No module symbols loaded - **kernel modules not enabled**.
thinking out loud: maybe you forgot to enable module support in your kernel config? is that possible?

---

### Post by eeyore on 2006-05-18
[QUOTE=towsonu2003]thinking out loud: maybe you forgot to enable module support in your kernel config? is that possible?[/QUOTE]

Nope it's all there:
MODULES
MODULES_UNLOAD
MODULE_FORCE_UNLOAD
MODVERSIONS
MODULE_SRCVERSION_ALL
KMOD

I also copied the old config into the new kernel so all of that should be included by default. I did remove a bunch of stuff but I researched a lot about what my hardware is. I removed only stuff that I don't need I'm pretty sure.

---

