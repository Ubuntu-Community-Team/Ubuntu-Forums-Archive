---
title: "SMBus"
date: 2010-05-07
forum: General Help
---

### Post by Praxicoide on 2010-05-07
Hi. I have a laptop that I can't get to boot any kernel beyond 2.6.30. This means, of course, that I'm stuck with Jaunty.

I've tried booting with karmic and lucid, with all boot parameters that I know of (noapic, acpi=off, nomodeset, etc) and all possible combinations and no luck. All result in a kernel panic and a "Machine check exception"

This is not a hardware problem, as the message implies, because I can boot with the 2.6.30 kernel (or earlier) with zero problems, and no crashes.


I'm trying to look at what changed in the kernel, but I'm not finding anything of much use. However, there is a message that I get when booting it's:

```
vt596_smbus 0000:00:07.4: SMBUS: Error: Host SMBus controller not enabled! – upgrade BIOS or use force=1 
```

Now, I don't know how to upgrade the BIOS, because all Sony gives me (this is an old Vaio laptop) is a windows utility.

But I'm trying to see the part about forcing the controller.

Putting

lspci -v

gives me this relevant part:
```

ISA bride: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 30)
Flags: medium devsel, IRQ 9
Capabilities: <access denied>
Kernel driver in use: vt596_smbus
Kernel modules: via686a, i2c-viapro
```

So I force the modules to load with modprobe -f, and all seems to go well, I mean, I don't get any crashes or anything. And I check with lsmod and they are show to be loaded.

But I reboot and I get the same message. I try lsmod, and they are still loaded, so I don't know what to do. Am I supposed to force the driver to load? How do I do that?

And could this really be the reason why I can't boot off any newer kernel?

---

